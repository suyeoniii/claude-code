# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains custom Claude Code commands and hooks for development workflow automation. The commands are written in Korean and focus on code review, optimization analysis, PR description generation, and testing for TypeScript/NestJS projects.

## Custom Commands

The repository provides four main custom commands in the `commands/` directory:

### `/optimize` - Performance Optimization Analysis
- Analyzes code changes for performance improvements
- Supports branch diff, PR analysis, and specific file analysis
- Focuses on database queries, memory usage, algorithms, caching, async processing, and NestJS/Prisma optimizations
- Can auto-comment on PRs with `--comment` flag

### `/review` - Code Review and Improvement Suggestions  
- Comprehensive code review covering quality, security, TypeScript/NestJS best practices, testing, architecture, and database
- Includes Claude CLI response verification for Korean language requirements and project context accuracy
- Supports PR auto-commenting functionality

### `/pr-description` - Automated PR Description Generation
- Analyzes PR changes and generates detailed descriptions based on templates
- Categorizes changes as additions, modifications, or refactoring
- Can automatically update PR descriptions with `--update` flag
- Uses GitHub CLI for PR operations

### `/test` - Test Code Generation and Execution
- Creates comprehensive tests using Jest and NestJS Testing Module
- Follows Given-When-Then structure with Korean test descriptions
- Covers unit tests, integration tests, edge cases, and proper mocking
- Uses `npm test` command for execution

## Development Setup

### Code Formatting
- Prettier hook is configured to automatically format TypeScript files on Edit/MultiEdit/Write operations
- Hook configuration located in `hooks/prettier.json`

### Language Requirements  
- All command descriptions and test descriptions should be written in **Korean**
- Function names and technical terms remain in English
- Commands expect Korean language output for consistency

### Architecture Patterns
- Commands are designed for TypeScript/NestJS projects
- Database operations assume Prisma ORM usage
- Testing framework: Jest with NestJS Testing Module
- Git workflow integration via GitHub CLI

## Common Development Tasks

Since this is a command definitions repository, the main development tasks involve:
- Editing command definitions in `commands/*.md`
- Modifying hook configurations in `hooks/*.json`
- Testing command functionality with actual TypeScript/NestJS projects

## Command Usage Patterns

All commands support flexible input patterns:
- PR numbers (numeric): Uses `gh pr view` and `gh pr diff`
- Branch names: Uses `git diff main..branch-name` 
- File paths: Direct file analysis
- No arguments: Uses `git diff main..HEAD`

Commands with `--comment` flag automatically post results as PR comments using `gh pr comment`.