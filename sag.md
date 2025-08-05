# SAG (Service API Gateway)

Main component of [SAS](sas.md) which manages accounts and services. 
It is Spring Boot application with frontend generation via Thymeleaf.
It has three modules: [AMS](#ams-account-managment-system), [APM](#apm-access-proxy-module) and [MSM](#msm-meta-service-manager).

## AMS (Account Managment System)

Module which manages accounts (creating, editing, fetching data to [SAS Services](sas.md#sas-services), ...). Provides `gRPC` interface and [SAS Services](sas.md#sas-services) can fetch data about accounts via this interface.

From client it is accessible through `/account` prefix.

## APM (Access Proxy Module)

Module for resending incomming requests to [SAS Services](sas.md#sas-services). 

This module does not have special prefix for itself but every [SAS Service](sas.md#sas-services) must have unique prefix. So if first part of `URL` does not match any other module, it falls to `APM` and `APM` will try to find [SAS Service](sas.md#sas-services) corresponding the prefix.

From client it is accessible through `/{servicePrefix}/**` prefix.

## MSM (Meta Service Manager)