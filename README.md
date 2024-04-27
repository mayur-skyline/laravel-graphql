# GraphQL with Laravel Project README

## GraphQL Overview

- GraphQL is a query language for APIs that provides a complete and understandable description of the data in your API.
- It allows clients to request only the data they need, making it easier to evolve APIs over time and enabling powerful developer tools.
- GraphQL facilitates CRUD (Create, Read, Update, Delete) operations in databases.

## Technology and Versions

- Laravel Version: 10
- GraphQL Version: 3.1
- Lighthouse: 6.31

## Installation

1. Install or update laravel composer:
    - composer update

2. Install Lighthouse (A framework for serving GraphQL from Laravel) via Composer:

    - composer require nuwave/lighthouse
    - php artisan vendor:publish --tag=lighthouse-schema
    
3. Install GraphQL DevTools:
    
    - composer require mll-lab/laravel-graphiql

4. Set environment variables and create the necessary database.

## Accessing GraphQL Tool

- Use the following URL (default) to access the GraphQL tool:
    - http://your-graphql-server/graphiql

## Demo Data Setup

- Run the following command to seed demo data:
    
    php artisan migrate:fresh --seed
    

## GraphQL Demo Queries

# Fetch Multiple Data with Pagination

    query{
        userslist(first:2 page:3){
            data{
                id
                email
                name
            }
            paginatorInfo{
                firstItem
                total
                hasMorePages
            }
        }
    }

# fetch single data 
    query{
        user(email:"test@gmail.com"){
            id
            name
            email
        }
    }
    
#fetch single data using userById
    query{
        userById(id:11){
            id
            name
            email
        }
    }

#create and check validation using Mutation
    mutation{
        createUser(
            input:{
            name:"test"
                    email:"test@gmail.com"
                    password:"password"
            }
        ){
            id
            name
            email
        }
    }
#update and check validation using Mutation
    mutation{
        updateUser(id:14
            input:{
            name:"test-testupdated"
                    password:"password"
            }
        ){
            id
            name
            email
        }
    }

#DELETE and check validation using Mutation
    mutation {
        deleteUser(id:12) {
            id
            name
            email
        }
    }
