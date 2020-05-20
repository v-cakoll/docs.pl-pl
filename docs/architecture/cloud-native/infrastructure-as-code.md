---
title: Infrastruktura jako kod
description: Wdrażanie infrastruktury jako kodu (IaC) z aplikacjami natywnymi w chmurze
ms.date: 05/13/2020
ms.openlocfilehash: cfc9e1f0b2733048d5921de5a0400998c282b1fa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613957"
---
# <a name="infrastructure-as-code"></a>Infrastruktura jako kod

Systemy natywne w chmurze uwzględniają mikrousługi, kontenery i nowoczesne projektowanie systemu, aby osiągnąć szybkość i elastyczność. Zapewniają one automatyczne etapy kompilowania i wydawania, aby zapewnić spójność i jakość kodu. Ale jest to tylko część wątku. Jak można zainicjować obsługę środowisk w chmurze, na których są uruchamiane te systemy?

Nowoczesne aplikacje natywne w chmurze stosują powszechnie zaakceptowane metody [infrastruktury jako kodu](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)lub `IaC` .  Przy użyciu IaC można zautomatyzować Inicjowanie obsługi platformy. Zasadniczo stosowane są praktyki inżynieryjne dotyczące oprogramowania, takie jak testowanie i przechowywanie wersji, do Twoich praktyk DevOps. Infrastruktura i wdrożenia są zautomatyzowane, spójne i powtarzalne. Podobnie jak ciągłe dostarczanie zautomatyzowany tradycyjny model wdrożeń ręcznych, infrastruktura jako kod (IaC) to ewolucja sposobu zarządzania środowiskami aplikacji.

Narzędzia takie jak Azure Resource Manager (ARM), Terraform i interfejs wiersza polecenia platformy Azure (CLI) umożliwiają deklaratywne skrypt wymaganej infrastruktury chmurowej.

## <a name="azure-resource-manager-templates"></a>Szablony usługi Azure Resource Manager

Dla [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/). Jest to aparat aprowizacji interfejsu API, który jest wbudowany w platformę Azure i udostępniany jako usługa interfejsu API. Usługa ARM umożliwia wdrażanie, aktualizowanie, usuwanie i zarządzanie zasobami zawartymi w grupie zasobów platformy Azure w ramach jednej, skoordynowanej operacji. Zapewniasz aparat z szablonem opartym na notacji JSON, który określa wymagane zasoby i ich konfigurację. ARM automatycznie organizuje wdrożenie w odpowiedniej kolejności z uwzględnieniem zależności. Aparat zapewnia idempotentności. Jeśli żądany zasób już istnieje z tą samą konfiguracją, Inicjowanie obsługi zostanie zignorowane.

Szablony Azure Resource Manager to język oparty na notacji JSON służący do definiowania różnych zasobów na platformie Azure. Schemat podstawowy wygląda podobnie do ilustracji 10-14.

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

**Rysunek 10-14** — schemat szablonu Menedżer zasobów

W ramach tego szablonu, jeden może zdefiniować kontener magazynu w sekcji Resources, tak więc:

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

**Rysunek 10-15** . przykład konta magazynu zdefiniowanego w szablonie Menedżer zasobów

Szablon ARM można sparametryzowane przy użyciu dynamicznego środowiska i informacji o konfiguracji. Dzięki temu można ponownie użyć do definiowania różnych środowisk, takich jak programowanie, pytania i odpowiedzi lub produkcja. Normalnie szablon tworzy wszystkie zasoby w ramach jednej grupy zasobów platformy Azure. Istnieje możliwość zdefiniowania wielu grup zasobów w jednym szablonie Menedżer zasobów, jeśli jest to konieczne. Wszystkie zasoby w środowisku można usunąć, usuwając samą grupę zasobów. Analiza kosztów może być również uruchamiana na poziomie grupy zasobów, co pozwala na szybkie księgowanie ilości kosztów poszczególnych środowisk.

Istnieje wiele przykładów lub szablonów usługi ARM dostępnych w projekcie [szablonów szybkiego startu platformy Azure](https://github.com/Azure/azure-quickstart-templates) w witrynie GitHub. Mogą pomóc przyspieszyć tworzenie nowego szablonu lub zmodyfikować istniejący.

Szablony Menedżer zasobów można uruchamiać na wiele sposobów. Prawdopodobnie najprostszym sposobem jest po prostu wklejenie ich do Azure Portal. W przypadku wdrożeń eksperymentalnych ta metoda może być szybka. Mogą być również uruchamiane jako część procesu kompilowania lub wydawania wersji w usłudze Azure DevOps. Istnieją zadania, które będą korzystać z połączeń na platformie Azure w celu uruchamiania szablonów. Zmiany w szablonach Menedżer zasobów są stosowane przyrostowo, co oznacza, że dodanie nowego zasobu wymaga tylko dodania go do szablonu. Narzędzia spowodują uzgodnienie różnic między bieżącymi zasobami a tymi zdefiniowanymi w szablonie. Zasoby zostaną następnie utworzone lub zmienione, aby były zgodne z tym, co zostało zdefiniowane w szablonie.  

## <a name="terraform"></a>Terraform

Aplikacje natywne w chmurze są często skonstruowane w taki sposób, aby były `cloud agnostic` . Oznacza to, że aplikacja nie jest ściśle połączona z konkretnym dostawcą chmury i można ją wdrożyć w dowolnej chmurze publicznej.

[Terraform](https://www.terraform.io/) to komercyjne narzędzie tworzenia szablonów, które umożliwia udostępnianie aplikacji natywnych w chmurze dla wszystkich głównych graczy w chmurze: Azure, Google Cloud Platform, AWS i AliCloud. Zamiast używać formatu JSON jako języka definicji szablonu, wykorzystuje nieco więcej zwięzła YAML.

Przykładowy plik Terraform, który jest taki sam jak poprzedni szablon Menedżer zasobów (Rysunek 10-15) przedstawiono na rysunku 10-16:

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

**Rysunek 10-16** — przykład szablonu Menedżer zasobów

Terraform udostępnia również intuicyjne komunikaty o błędach dla szablonów problemów. Istnieje również przydatne zadanie sprawdzania poprawności, które może być używane w fazie kompilacji do wczesnego przechwytywania błędów szablonów.

Podobnie jak w przypadku szablonów Menedżer zasobów, narzędzia wiersza polecenia są dostępne do wdrażania szablonów Terraform. Istnieją również zadania utworzone przez społeczność w Azure Pipelines, które mogą weryfikować i stosować szablony Terraform.

Czasami szablony Terraform i ARM wyprowadzają znaczące wartości, takie jak parametry połączenia do nowo utworzonej bazy danych. Te informacje mogą być przechwytywane w potoku kompilacji i używane w kolejnych zadaniach.

## <a name="azure-cli-scripts-and-tasks"></a>Skrypty i zadania interfejsu wiersza polecenia platformy Azure

Na koniec możesz użyć [interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/cli/azure/) , aby deklaratywnie zaskryptować infrastrukturę chmurową. Skrypty interfejsu wiersza polecenia platformy Azure mogą być tworzone, dostępne i udostępniane w celu aprowizacji i konfigurowania niemal dowolnych zasobów platformy Azure. Interfejs wiersza polecenia jest prosty do użycia z łagodną krzywą uczenia się. Skrypty są wykonywane w ramach programu PowerShell lub bash. Są one również proste do debugowania, szczególnie w porównaniu z szablonami ARM.

Skrypty interfejsu wiersza polecenia platformy Azure działają prawidłowo, gdy konieczne jest rozbicie i ponowne wdrożenie infrastruktury. Aktualizowanie istniejącego środowiska może być trudne. Wiele poleceń interfejsu wiersza polecenia nie jest idempotentne. Oznacza to, że będą ponownie tworzyć zasób przy każdym uruchomieniu, nawet jeśli zasób już istnieje. Zawsze jest możliwe dodanie kodu, który sprawdza obecność poszczególnych zasobów przed utworzeniem go. Jednak dzięki temu skrypt może być bloated i trudny do zarządzania.

Te skrypty można także osadzić w potokach usługi Azure DevOps jako `Azure CLI tasks` . Wykonanie potoku wywołuje skrypt.

Na rysunku 10-17 przedstawiono fragment kodu YAML, który zawiera listę wersji interfejsu wiersza polecenia platformy Azure oraz szczegóły subskrypcji. Zwróć uwagę na to, jak w skrypcie wbudowanym znajdują się polecenia interfejsu CLI platformy Azure.

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

**Rysunek 10-17** — skrypt interfejsu wiersza polecenia platformy Azure

W artykule [co to jest infrastruktura jako kod](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), autor sam Guckenheimer opisuje, jak "zespoły, które implementują IaC, mogą szybko i w odpowiedniej skali. Zespoły unikają ręcznej konfiguracji środowisk i wymuszania spójności przez odzwierciedlenie żądanego stanu środowiska za pośrednictwem kodu. Wdrożenia infrastruktury za pomocą IaC są powtarzalne i zapobiegają problemom z czasem wykonywania spowodowanym przez dryfowanie konfiguracji lub brakujące zależności. Zespoły DevOps mogą współdziałać z ujednoliconym zestawem praktyk i narzędzi, aby dostarczać aplikacje i obsługiwać infrastrukturę szybko, niezawodnie i na dużą skalę. "

>[!div class="step-by-step"]
>[Poprzedni](feature-flags.md) 
> [Dalej](application-bundles.md)
