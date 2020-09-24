Demo2 Common Components and Definitions
=======================================

The second blockchain demo consists of three applications. The first is a
simple UI that displays the current component state and allows the user to set
the desired state for this component, namely either "on" or "off".  The second
application is a daemon that controls the component. This can either be a
virtual application, or it can be deployed on a Raspberry Pi Zero W to control a
relay. The third application is a simple setup application, which can be used
along with vctool to bootstrap the demo.  More information about these
applications can be found in their respective respositories.

The common component repository defines methods that can be used to create and
sign transaction certificates for the transactions supported by this demo.

Artifact Types and Transaction Types
------------------------------------

This demo supports the following entity / artifact types:

| Entity name       | Artifact type                        |
|:------------------|:------------------------------------:|
| Controller        | dd6f7017-f4d5-4ce9-a71a-12ff0a77b1fd |
| Component         | 3e528784-2f99-40c3-b325-19abdf2d7108 |

This demo supports the following transactions:

| Transaction name  | Transaction type                     | Description                         |
|:------------------|:------------------------------------:|:------------------------------------|
| Controller create | e8884c8d-e067-4d22-8884-088bf16093be | creates a controller entity.        |
| Controller destroy| 94a957c8-747e-41cc-a6fa-fae73393a8a4 | destroys a controller entity.       |
| Component create  | 541b94e5-f0bf-43ca-a503-f4ad7d8acb32 | creates a component entity.         |
| Component destroy | 7578b756-06d5-49f1-a7dc-4bd288a60774 | destroys a component entity.        |
| state change req  | 09afc44f-faed-41b8-a5cc-d45a4e707afe | Request component change state.     |
| state change ack  | 8f97ef23-cfd2-4586-b085-9b682f916d17 | Acknowledge component state change. |
