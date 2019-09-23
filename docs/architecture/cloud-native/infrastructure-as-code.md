---
title: Infrastruktura jako kod
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Infrastruktura jako kod
ms.date: 06/30/2019
ms.openlocfilehash: e395db28bdeff785251b91ed643f9920873d26e8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183015"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="e12b3-103">Infrastruktura jako kod</span><span class="sxs-lookup"><span data-stu-id="e12b3-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e12b3-104">Aplikacje natywne w chmurze mogą korzystać ze wszystkich rodzajów składników fantastycznie platformy jako usługi (PaaS).</span><span class="sxs-lookup"><span data-stu-id="e12b3-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="e12b3-105">Na platformie w chmurze, takiej jak platforma Azure, te składniki mogą obejmować takie elementy jak magazyn, Service Bus i usługa sygnalizująca.</span><span class="sxs-lookup"><span data-stu-id="e12b3-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="e12b3-106">W miarę jak aplikacje stają się bardziej skomplikowane, liczba tych usług jest prawdopodobnie większa.</span><span class="sxs-lookup"><span data-stu-id="e12b3-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="e12b3-107">Podobnie jak w przypadku ciągłego dostarczania tradycyjnego modelu wdrażania do środowiska, szybkim tempem zmian może być również problem z modelem scentralizowanej grupy IT do zarządzania środowiskami.</span><span class="sxs-lookup"><span data-stu-id="e12b3-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="e12b3-108">Środowiska budynku mogą, a także być zautomatyzowane.</span><span class="sxs-lookup"><span data-stu-id="e12b3-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="e12b3-109">Istnieje szeroki zakres dobrze przemyślanych narzędzi, które mogą ułatwić proces.</span><span class="sxs-lookup"><span data-stu-id="e12b3-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="e12b3-110">Szablony Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="e12b3-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="e12b3-111">Szablony Azure Resource Manager to język oparty na notacji JSON służący do definiowania różnych zasobów na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="e12b3-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="e12b3-112">Schemat podstawowy wygląda podobnie do ilustracji 11-10.</span><span class="sxs-lookup"><span data-stu-id="e12b3-112">The basic schema looks something like Figure 11-10.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="e12b3-113">**Rysunek 11-10** — schemat szablonu Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="e12b3-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="e12b3-114">W ramach tego szablonu, jeden może zdefiniować kontener magazynu w sekcji Resources, tak więc:</span><span class="sxs-lookup"><span data-stu-id="e12b3-114">Within this template, one might define a storage container inside the resources section like so:</span></span>
 
```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="e12b3-115">**Rysunek 11-11** . przykład konta magazynu zdefiniowanego w szablonie Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="e12b3-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="e12b3-116">Szablony mogą być sparametryzowane, aby można było użyć jednego szablonu z różnymi ustawieniami w celu zdefiniowania środowisk programistycznych, pytań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e12b3-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="e12b3-117">Pomaga to wyeliminować niezależności podczas migracji do wyższego środowiska, które jest skonfigurowane inaczej niż w przypadku małych środowisk.</span><span class="sxs-lookup"><span data-stu-id="e12b3-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="e12b3-118">Zasoby zdefiniowane w szablonie są zwykle tworzone w ramach jednej grupy zasobów na platformie Azure (można zdefiniować wiele grup zasobów w jednym szablonie Menedżer zasobów, ale nietypowe).</span><span class="sxs-lookup"><span data-stu-id="e12b3-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="e12b3-119">Dzięki temu można łatwo usunąć środowisko przez usunięcie grupy zasobów jako całości.</span><span class="sxs-lookup"><span data-stu-id="e12b3-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="e12b3-120">Analiza kosztów może być również uruchamiana na poziomie grupy zasobów, co pozwala na szybkie księgowanie ilości kosztów poszczególnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="e12b3-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="e12b3-121">Istnieje wiele przykładowych szablonów zdefiniowanych w projekcie [szablonów szybkiego startu platformy Azure](https://github.com/Azure/azure-quickstart-templates) w witrynie GitHub, które będą stanowić podstawę w przypadku uruchamiania na nowym szablonie lub dodania do istniejącej.</span><span class="sxs-lookup"><span data-stu-id="e12b3-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="e12b3-122">Szablony Menedżer zasobów można uruchamiać na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="e12b3-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="e12b3-123">Prawdopodobnie najprostszym sposobem jest po prostu wklejenie ich do Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e12b3-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="e12b3-124">W przypadku wdrożeń eksperymentalnych ta metoda może być bardzo szybka.</span><span class="sxs-lookup"><span data-stu-id="e12b3-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="e12b3-125">Mogą być również uruchamiane jako część procesu kompilowania lub wydawania wersji w usłudze Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="e12b3-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="e12b3-126">Istnieją zadania, które będą korzystać z połączeń na platformie Azure w celu uruchamiania szablonów.</span><span class="sxs-lookup"><span data-stu-id="e12b3-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="e12b3-127">Zmiany w szablonach Menedżer zasobów są stosowane przyrostowo, co oznacza, że dodanie nowego zasobu wymaga tylko dodania go do szablonu.</span><span class="sxs-lookup"><span data-stu-id="e12b3-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="e12b3-128">Narzędzia będą obsługiwać różnicowanie bieżącej grupy zasobów z żądaną grupą zasobów zdefiniowaną w szablonie.</span><span class="sxs-lookup"><span data-stu-id="e12b3-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="e12b3-129">Zasoby zostaną następnie utworzone lub zmienione, aby były zgodne z tym, co zostało zdefiniowane w szablonie.</span><span class="sxs-lookup"><span data-stu-id="e12b3-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="e12b3-130">Terraform</span><span class="sxs-lookup"><span data-stu-id="e12b3-130">Terraform</span></span>

<span data-ttu-id="e12b3-131">Postrzegana wada Menedżer zasobów szablonów polega na tym, że są one specyficzne dla chmury platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="e12b3-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="e12b3-132">Nie ma potrzeby tworzenia aplikacji, które obejmują zasoby z więcej niż jednej chmury, ale w przypadkach, w których działalność biznesowa opiera się na spektakularnych czasowym, koszt obsługi wielu chmur może być wartościowa.</span><span class="sxs-lookup"><span data-stu-id="e12b3-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="e12b3-133">W przypadku użycia jednego języka tworzenia szablonów, który może być używany w każdej chmurze, można także zapewnić, że kwalifikacje deweloperów będą znacznie bardziej przenośne.</span><span class="sxs-lookup"><span data-stu-id="e12b3-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="e12b3-134">Istnieje kilka technologii, które wystarczy!</span><span class="sxs-lookup"><span data-stu-id="e12b3-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="e12b3-135">Najbardziej dojrzała oferta w tym miejscu jest znana jako [Terraform](https://www.terraform.io/).</span><span class="sxs-lookup"><span data-stu-id="e12b3-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="e12b3-136">Usługa Terraform obsługuje każdy główny odtwarzacz w chmurze, taki jak Azure, Google Cloud Platform, AWS i AliCloud, a także obsługuje dziesiątki drobnych odtwarzaczy, takich jak Heroku i DigitalOcean.</span><span class="sxs-lookup"><span data-stu-id="e12b3-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="e12b3-137">Zamiast używać formatu JSON jako języka definicji szablonu, wykorzystuje nieco więcej zwięzła YAML.</span><span class="sxs-lookup"><span data-stu-id="e12b3-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span> 

<span data-ttu-id="e12b3-138">Przykładowy plik Terraform, który jest taki sam jak poprzedni szablon Menedżer zasobów (Rysunek 11-11) przedstawiono na rysunku 11-12:</span><span class="sxs-lookup"><span data-stu-id="e12b3-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="e12b3-139">**Rysunek 11-12** — przykład szablonu Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="e12b3-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="e12b3-140">Terraform wykonuje lepsze zadanie zapewniania rozsądnych komunikatów o błędach, gdy nie można wdrożyć zasobu z powodu błędu w szablonie.</span><span class="sxs-lookup"><span data-stu-id="e12b3-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="e12b3-141">Jest to obszar, w którym Menedżer zasobów szablony mają pewne ciągłe wyzwania.</span><span class="sxs-lookup"><span data-stu-id="e12b3-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="e12b3-142">Istnieje również bardzo przydatne zadanie sprawdzania poprawności, które może być używane w fazie kompilacji do wczesnego przechwytywania błędów szablonów.</span><span class="sxs-lookup"><span data-stu-id="e12b3-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="e12b3-143">Podobnie jak w przypadku szablonów Menedżer zasobów, dostępne są narzędzia wiersza polecenia, których można użyć do wdrożenia szablonów Terraform.</span><span class="sxs-lookup"><span data-stu-id="e12b3-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="e12b3-144">Istnieją również zadania utworzone przez społeczność w Azure Pipelines, które mogą weryfikować i stosować szablony Terraform.</span><span class="sxs-lookup"><span data-stu-id="e12b3-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="e12b3-145">W przypadku, gdy szablon Terraform lub Menedżer zasobów wyprowadza interesujące wartości, takie jak parametry połączenia, do nowo utworzonej bazy danych, które mogą być przechwytywane w potoku kompilacji i używane w kolejnych zadaniach.</span><span class="sxs-lookup"><span data-stu-id="e12b3-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e12b3-146">[Poprzedni](devops.md)
>[Następny](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="e12b3-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
