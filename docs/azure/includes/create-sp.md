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
<span data-ttu-id="dbcf7-101">Aplikacja platformy .NET musi mieć uprawnienia do odczytu i tworzenia zasobów w ramach subskrypcji platformy Azure, aby można było korzystać z bibliotek zarządzania platformy Azure dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-101">Your .NET application needs permissions to read and create resources in your Azure subscription in order to use the Azure Management Libraries for .NET.</span></span> <span data-ttu-id="dbcf7-102">Utwórz nazwę główną usługi i skonfiguruj aplikację do uruchamiania z poświadczeniami, aby udzielić dostępu.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-102">Create a service principal and configure your app to run with its credentials to grant this access.</span></span> <span data-ttu-id="dbcf7-103">Jednostki usługi oferują sposób tworzenia nieinterakcyjnego konta skojarzonego z tożsamością, któremu przyznawane są tylko uprawnienia wymagane do działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-103">Service principals provide a way to create a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="dbcf7-104">Najpierw Zaloguj się do [Azure Cloud Shell](https://shell.azure.com/bash).</span><span class="sxs-lookup"><span data-stu-id="dbcf7-104">First, login to [Azure Cloud Shell](https://shell.azure.com/bash).</span></span> <span data-ttu-id="dbcf7-105">Sprawdź, czy korzystasz obecnie z subskrypcji, w której ma zostać utworzona nazwa główna usługi.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-105">Verify you are currently using the subscription in which you want the service principal created.</span></span>

```azurecli-interactive
az account show
```

<span data-ttu-id="dbcf7-106">Zostaną wyświetlone informacje o subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-106">Your subscription information is displayed.</span></span>

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

<span data-ttu-id="dbcf7-107">Jeśli nie zalogowano się do poprawnej subskrypcji, wybierz odpowiednią wartość, wpisując `az account set -s <name or ID of subscription>`.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-107">If you're not logged into the correct subscription, select the correct one by typing `az account set -s <name or ID of subscription>`.</span></span>

<span data-ttu-id="dbcf7-108">Utwórz jednostkę usługi za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="dbcf7-108">Create the service principal with the following command:</span></span>

```azurecli-interactive
az ad sp create-for-rbac --sdk-auth
```

<span data-ttu-id="dbcf7-109">Informacje o jednostce usługi są wyświetlane jako dane JSON.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-109">The service principal information is displayed as JSON.</span></span>

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

<span data-ttu-id="dbcf7-110">Skopiuj i wklej dane wyjściowe JSON do edytora tekstów w celu późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="dbcf7-110">Copy and paste the JSON output to a text editor for use later.</span></span>
