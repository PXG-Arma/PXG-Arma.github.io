#
# Compiles all PHP files in the current working directory to HTML in
# the build directory. Uses PHP files in the lib directory as dependencies.
#
# Syncs the compiled HTML files to the repo root based on file checksums.
#
# Dependencies:
# * php
# * rsync
#

# Directory to write compiled HTML pages into
BUILD_DIR = build
# Directory containing PHP library files
PHP_LIB_DIR = include
# Path to the root of the static web site repository
REPO_PATH = ../
# PHP executable to use
PHP = php

# PHP libraries required to process the sources
PHP_LIBS := $(wildcard $(PHP_LIB_DIR)/*.php)
# PHP source files to process with PHP to HTML
PHP_SOURCES := $(wildcard *.php)
# Target HTML files in the build directory
HTML_PAGES := $(addprefix $(BUILD_DIR)/,$(PHP_SOURCES:.php=.html))

.PHONY: html clean sync

# Compiles all PHP sources to HTML
html: $(HTML_PAGES)

# Processes a .php file with PHP to produce HTML file
$(BUILD_DIR)/%.html: %.php $(PHP_LIBS) | $(BUILD_DIR)
	$(PHP) -f '$<' > '$@'

# Creates the build directory
$(BUILD_DIR):
	mkdir -p $@

# Removes the build directory
clean:
	rm -rf $(BUILD_DIR)

# Syncs the HTML files to the repo
sync: html
	rsync -aic 'build/' $(REPO_PATH)

