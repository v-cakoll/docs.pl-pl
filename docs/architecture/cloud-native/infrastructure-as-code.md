---
title: Infrastruktura jako kod
description: Wdrażanie infrastruktury jako kodu (IaC) z aplikacjami natywnymi w chmurze
ms.date: 05/12/2020
ms.openlocfilehash: 309dd8610ab3b72a6c6da5297f109f822520c5ff
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395345"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="03867-103">Infrastruktura jako kod</span><span class="sxs-lookup"><span data-stu-id="03867-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="03867-104">Systemy natywne w chmurze uwzględniają mikrousługi, kontenery i nowoczesne projektowanie systemu, aby osiągnąć szybkość i elastyczność.</span><span class="sxs-lookup"><span data-stu-id="03867-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="03867-105">Zapewniają one automatyczne etapy kompilowania i wydawania, aby zapewnić spójność i jakość kodu.</span><span class="sxs-lookup"><span data-stu-id="03867-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="03867-106">Ale jest to tylko część wątku.</span><span class="sxs-lookup"><span data-stu-id="03867-106">But, that's only part of the story.</span></span> <span data-ttu-id="03867-107">Jak można zainicjować obsługę środowisk w chmurze, na których są uruchamiane te systemy?</span><span class="sxs-lookup"><span data-stu-id="03867-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="03867-108">Nowoczesne aplikacje natywne w chmurze stosują powszechnie zaakceptowane metody [infrastruktury jako kodu](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)lub `IaC` .</span><span class="sxs-lookup"><span data-stu-id="03867-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="03867-109">Przy użyciu IaC można zautomatyzować Inicjowanie obsługi platformy.</span><span class="sxs-lookup"><span data-stu-id="03867-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="03867-110">Zasadniczo stosowane są praktyki inżynieryjne dotyczące oprogramowania, takie jak testowanie i przechowywanie wersji, do Twoich praktyk DevOps.</span><span class="sxs-lookup"><span data-stu-id="03867-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="03867-111">Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne.</span><span class="sxs-lookup"><span data-stu-id="03867-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="03867-112">Podobnie jak ciągłe dostarczanie zautomatyzowany tradycyjny model wdrożeń ręcznych, infrastruktura jako kod (IaC) to ewolucja sposobu zarządzania środowiskami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03867-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="03867-113">Narzędzia takie jak Azure Resource Manager (ARM), Terraform i interfejs wiersza polecenia platformy Azure (CLI) umożliwiają deklaratywne skrypt wymaganej infrastruktury chmurowej.</span><span class="sxs-lookup"><span data-stu-id="03867-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="03867-114">Szablony usługi Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="03867-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="03867-115">Dla [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span><span class="sxs-lookup"><span data-stu-id="03867-115">ARM stands for [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span></span> <span data-ttu-id="03867-116">Jest to aparat aprowizacji interfejsu API, który jest wbudowany w platformę Azure i udostępniany jako usługa interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="03867-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="03867-117">Usługa ARM umożliwia wdrażanie, aktualizowanie, usuwanie i zarządzanie zasobami zawartymi w grupie zasobów platformy Azure w ramach jednej, skoordynowanej operacji.</span><span class="sxs-lookup"><span data-stu-id="03867-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="03867-118">Zapewniasz aparat z szablonem opartym na notacji JSON, który określa wymagane zasoby i ich konfigurację.</span><span class="sxs-lookup"><span data-stu-id="03867-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="03867-119">ARM automatycznie organizuje wdrożenie w odpowiedniej kolejności z uwzględnieniem zależności.</span><span class="sxs-lookup"><span data-stu-id="03867-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="03867-120">Aparat zapewnia idempotentności.</span><span class="sxs-lookup"><span data-stu-id="03867-120">The engine ensures idempotency.</span></span> <span data-ttu-id="03867-121">Jeśli żądany zasób już istnieje z tą samą konfiguracją, Inicjowanie obsługi zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="03867-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="03867-122">Szablony Azure Resource Manager to język oparty na notacji JSON służący do definiowania różnych zasobów na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="03867-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="03867-123">Schemat podstawowy wygląda podobnie do ilustracji 10-14.</span><span class="sxs-lookup"><span data-stu-id="03867-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="03867-124">**Rysunek 10-14** — schemat szablonu Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="03867-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="03867-125">W ramach tego szablonu, jeden może zdefiniować kontener magazynu w sekcji Resources, tak więc:</span><span class="sxs-lookup"><span data-stu-id="03867-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="03867-126">**Rysunek 10-15** . przykład konta magazynu zdefiniowanego w szablonie Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="03867-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="03867-127">Szablon ARM można sparametryzowane przy użyciu dynamicznego środowiska i informacji o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="03867-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="03867-128">Dzięki temu można ponownie użyć do definiowania różnych środowisk, takich jak programowanie, pytania i odpowiedzi lub produkcja.</span><span class="sxs-lookup"><span data-stu-id="03867-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="03867-129">Normalnie szablon tworzy wszystkie zasoby w ramach jednej grupy zasobów platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="03867-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="03867-130">Istnieje możliwość zdefiniowania wielu grup zasobów w jednym szablonie Menedżer zasobów, jeśli jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="03867-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="03867-131">Wszystkie zasoby w środowisku można usunąć, usuwając samą grupę zasobów.</span><span class="sxs-lookup"><span data-stu-id="03867-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="03867-132">Analiza kosztów może być również uruchamiana na poziomie grupy zasobów, co pozwala na szybkie księgowanie ilości kosztów poszczególnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="03867-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="03867-133">Istnieje wiele przykładów lub szablonów usługi ARM dostępnych w projekcie [szablonów szybkiego startu platformy Azure](https://github.com/Azure/azure-quickstart-templates) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="03867-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="03867-134">Mogą pomóc przyspieszyć tworzenie nowego szablonu lub zmodyfikować istniejący.</span><span class="sxs-lookup"><span data-stu-id="03867-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="03867-135">Szablony Menedżer zasobów można uruchamiać na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="03867-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="03867-136">Prawdopodobnie najprostszym sposobem jest po prostu wklejenie ich do Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="03867-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="03867-137">W przypadku wdrożeń eksperymentalnych ta metoda może być szybka.</span><span class="sxs-lookup"><span data-stu-id="03867-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="03867-138">Mogą być również uruchamiane jako część procesu kompilowania lub wydawania wersji w usłudze Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="03867-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="03867-139">Istnieją zadania, które będą korzystać z połączeń na platformie Azure w celu uruchamiania szablonów.</span><span class="sxs-lookup"><span data-stu-id="03867-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="03867-140">Zmiany w szablonach Menedżer zasobów są stosowane przyrostowo, co oznacza, że dodanie nowego zasobu wymaga tylko dodania go do szablonu.</span><span class="sxs-lookup"><span data-stu-id="03867-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="03867-141">Narzędzia spowodują uzgodnienie różnic między bieżącymi zasobami a tymi zdefiniowanymi w szablonie.</span><span class="sxs-lookup"><span data-stu-id="03867-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="03867-142">Zasoby zostaną następnie utworzone lub zmienione, aby były zgodne z tym, co zostało zdefiniowane w szablonie.</span><span class="sxs-lookup"><span data-stu-id="03867-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="03867-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="03867-143">Terraform</span></span>

<span data-ttu-id="03867-144">Aplikacje natywne w chmurze są często skonstruowane w taki sposób, aby były `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="03867-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="03867-145">Oznacza to, że aplikacja nie jest ściśle połączona z konkretnym dostawcą chmury i można ją wdrożyć w dowolnej chmurze publicznej.</span><span class="sxs-lookup"><span data-stu-id="03867-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="03867-146">[Terraform](https://www.terraform.io/) to komercyjne narzędzie tworzenia szablonów, które umożliwia udostępnianie aplikacji natywnych w chmurze dla wszystkich głównych graczy w chmurze: Azure, Google Cloud Platform, AWS i AliCloud.</span><span class="sxs-lookup"><span data-stu-id="03867-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="03867-147">Zamiast używać formatu JSON jako języka definicji szablonu, wykorzystuje nieco więcej zwięzła YAML.</span><span class="sxs-lookup"><span data-stu-id="03867-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="03867-148">Przykładowy plik Terraform, który jest taki sam jak poprzedni szablon Menedżer zasobów (Rysunek 10-15) przedstawiono na rysunku 10-16:</span><span class="sxs-lookup"><span data-stu-id="03867-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="03867-149">**Rysunek 10-16** — przykład szablonu Menedżer zasobów</span><span class="sxs-lookup"><span data-stu-id="03867-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="03867-150">Terraform udostępnia również intuicyjne komunikaty o błędach dla szablonów problemów.</span><span class="sxs-lookup"><span data-stu-id="03867-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="03867-151">Istnieje również przydatne zadanie sprawdzania poprawności, które może być używane w fazie kompilacji do wczesnego przechwytywania błędów szablonów.</span><span class="sxs-lookup"><span data-stu-id="03867-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="03867-152">Podobnie jak w przypadku szablonów Menedżer zasobów, narzędzia wiersza polecenia są dostępne do wdrażania szablonów Terraform.</span><span class="sxs-lookup"><span data-stu-id="03867-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="03867-153">Istnieją również zadania utworzone przez społeczność w Azure Pipelines, które mogą weryfikować i stosować szablony Terraform.</span><span class="sxs-lookup"><span data-stu-id="03867-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="03867-154">Czasami szablony Terraform i ARM wyprowadzają znaczące wartości, takie jak parametry połączenia do nowo utworzonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="03867-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="03867-155">Te informacje mogą być przechwytywane w potoku kompilacji i używane w kolejnych zadaniach.</span><span class="sxs-lookup"><span data-stu-id="03867-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="03867-156">Skrypty i zadania interfejsu wiersza polecenia platformy Azure</span><span class="sxs-lookup"><span data-stu-id="03867-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="03867-157">Na koniec możesz użyć [interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/cli/azure/) , aby deklaratywnie zaskryptować infrastrukturę chmurową.</span><span class="sxs-lookup"><span data-stu-id="03867-157">Finally, you can leverage [Azure CLI](https://docs.microsoft.com/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="03867-158">Skrypty interfejsu wiersza polecenia platformy Azure mogą być tworzone, dostępne i udostępniane w celu aprowizacji i konfigurowania niemal dowolnych zasobów platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="03867-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="03867-159">Interfejs wiersza polecenia jest prosty do użycia z łagodną krzywą uczenia się.</span><span class="sxs-lookup"><span data-stu-id="03867-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="03867-160">Skrypty są wykonywane w ramach programu PowerShell lub bash.</span><span class="sxs-lookup"><span data-stu-id="03867-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="03867-161">Są one również proste do debugowania, szczególnie w porównaniu z szablonami ARM.</span><span class="sxs-lookup"><span data-stu-id="03867-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="03867-162">Skrypty interfejsu wiersza polecenia platformy Azure działają prawidłowo, gdy konieczne jest rozbicie i ponowne wdrożenie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="03867-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="03867-163">Aktualizowanie istniejącego środowiska może być trudne.</span><span class="sxs-lookup"><span data-stu-id="03867-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="03867-164">Wiele poleceń interfejsu wiersza polecenia nie jest idempotentne.</span><span class="sxs-lookup"><span data-stu-id="03867-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="03867-165">Oznacza to, że będą ponownie tworzyć zasób przy każdym uruchomieniu, nawet jeśli zasób już istnieje.</span><span class="sxs-lookup"><span data-stu-id="03867-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="03867-166">Zawsze jest możliwe dodanie kodu, który sprawdza obecność poszczególnych zasobów przed utworzeniem go.</span><span class="sxs-lookup"><span data-stu-id="03867-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="03867-167">Jednak dzięki temu skrypt może być bloated i trudny do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="03867-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="03867-168">Te skrypty można także osadzić w potokach usługi Azure DevOps jako `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="03867-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="03867-169">Wykonanie potoku wywołuje skrypt.</span><span class="sxs-lookup"><span data-stu-id="03867-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="03867-170">Na rysunku 10-17 przedstawiono fragment kodu YAML, który zawiera listę wersji interfejsu wiersza polecenia platformy Azure oraz szczegóły subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="03867-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="03867-171">Zwróć uwagę na to, jak w skrypcie wbudowanym znajdują się polecenia interfejsu CLI platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="03867-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="03867-172">**Rysunek 10-17** — skrypt interfejsu wiersza polecenia platformy Azure</span><span class="sxs-lookup"><span data-stu-id="03867-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="03867-173">W artykule [co to jest infrastruktura jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), autor sam Guckenheimer opisuje, jak "zespoły, które implementują IaC, mogą szybko i w odpowiedniej skali.</span><span class="sxs-lookup"><span data-stu-id="03867-173">In the article, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="03867-174">Zespoły unikają ręcznej konfiguracji środowisk i wymuszania spójności przez odzwierciedlenie żądanego stanu środowiska za pośrednictwem kodu.</span><span class="sxs-lookup"><span data-stu-id="03867-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="03867-175">Wdrożenia infrastruktury za pomocą IaC są powtarzalne i zapobiegają problemom z czasem wykonywania spowodowanym przez dryfowanie konfiguracji lub brakujące zależności.</span><span class="sxs-lookup"><span data-stu-id="03867-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="03867-176">Zespoły DevOps mogą współdziałać z ujednoliconym zestawem praktyk i narzędzi, aby dostarczać aplikacje i obsługiwać infrastrukturę szybko, niezawodnie i na dużą skalę. "</span><span class="sxs-lookup"><span data-stu-id="03867-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="03867-177">[Poprzedni](feature-flags.md) 
> [Dalej](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="03867-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
