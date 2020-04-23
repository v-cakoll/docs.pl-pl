---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: c3746ff92838ac97d8158a0daf0b1a1de07ae024
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071984"
---
Aplikacja .NET potrzebuje uprawnień do odczytu i tworzenia zasobów w ramach subskrypcji platformy Azure w celu użycia bibliotek zarządzania platformy Azure dla platformy .NET. Utwórz jednostkę usługi i skonfiguruj aplikację do uruchamiania z jej poświadczeniami, aby udzielić tego dostępu. Jednostki usługi oferują sposób tworzenia nieinterakcyjnego konta skojarzonego z tożsamością, któremu przyznawane są tylko uprawnienia wymagane do działania aplikacji.

Najpierw zaloguj się do [usługi Azure Cloud Shell](https://shell.azure.com/bash). Sprawdź, czy aktualnie używasz subskrypcji, w której ma zostać utworzona jednostka usługi.

```azurecli-interactive
az account show
```

Wyświetlane są informacje o subskrypcji.

```json
{
  "environmentName": "AzureCloud",
  "id": "15dbcfa8-4b93-4c9a-881c-6189d39f04d4",
  "isDefault": true,
  "name": "my-subscription",
  "state": "Enabled",
  "tenantId": "43413cc1-5886-4711-9804-8cfea3d1c3ee",
  "user": {
    "cloudShellID": true,
    "name": "jane@contoso.com",
    "type": "user"
  }
}
```

Jeśli nie jesteś zalogowany do właściwej subskrypcji, wybierz `az account set -s <name or ID of subscription>`właściwą, wpisując .

Utwórz jednostkę usługi za pomocą następującego polecenia:

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

Informacje o jednostki usługi są wyświetlane jako JSON.

```json
{
  "clientId": "b52dd125-9272-4b21-9862-0be667bdf6dc",
  "clientSecret": "ebc6e170-72b2-4b6f-9de2-99410964d2d0",
  "subscriptionId": "ffa52f27-be12-4cad-b1ea-c2c241b6cceb",
  "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
  "resourceManagerEndpointUrl": "https://management.azure.com/",
  "activeDirectoryGraphResourceId": "https://graph.windows.net/",
  "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
  "galleryEndpointUrl": "https://gallery.azure.com/",
  "managementEndpointUrl": "https://management.core.windows.net/"
}
```

Kopiowanie i wklejanie danych wyjściowych JSON do edytora tekstu do późniejszego użycia.
