---
title: Infrastruktura jako kod
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Infrastruktura jako kod
ms.date: 06/30/2019
ms.openlocfilehash: 3957da68ac28774f899f49fb181a29c2435902f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087245"
---
# <a name="infrastructure-as-code"></a>Infrastruktura jako kod

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikacje natywne w chmurze mogą korzystać ze wszystkich rodzajów składników fantastycznie platformy jako usługi (PaaS). Na platformie w chmurze, takiej jak platforma Azure, te składniki mogą obejmować takie elementy jak magazyn, Service Bus i usługa sygnalizująca. W miarę jak aplikacje stają się bardziej skomplikowane, liczba tych usług jest prawdopodobnie większa. Podobnie jak w przypadku ciągłego dostarczania tradycyjnego modelu wdrażania do środowiska, szybkim tempem zmian może być również problem z modelem scentralizowanej grupy IT do zarządzania środowiskami.

Środowiska budynku mogą, a także być zautomatyzowane. Istnieje szeroki zakres dobrze przemyślanych narzędzi, które mogą ułatwić proces.

## <a name="azure-resource-manager-templates"></a>Szablony Azure Resource Manager

Szablony Azure Resource Manager to język oparty na notacji JSON służący do definiowania różnych zasobów na platformie Azure. Schemat podstawowy wygląda podobnie do ilustracji 11-10.

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

**Rysunek 11-10** — schemat szablonu Menedżer zasobów

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

**Rysunek 11-11** . przykład konta magazynu zdefiniowanego w szablonie Menedżer zasobów

Szablony mogą być sparametryzowane, aby można było użyć jednego szablonu z różnymi ustawieniami w celu zdefiniowania środowisk programistycznych, pytań i odpowiedzi. Pomaga to wyeliminować niezależności podczas migracji do wyższego środowiska, które jest skonfigurowane inaczej niż w przypadku małych środowisk. Zasoby zdefiniowane w szablonie są zwykle tworzone w ramach jednej grupy zasobów na platformie Azure (można zdefiniować wiele grup zasobów w jednym szablonie Menedżer zasobów, ale nietypowe). Dzięki temu można łatwo usunąć środowisko przez usunięcie grupy zasobów jako całości. Analiza kosztów może być również uruchamiana na poziomie grupy zasobów, co pozwala na szybkie księgowanie ilości kosztów poszczególnych środowisk.

Istnieje wiele przykładowych szablonów zdefiniowanych w projekcie [szablonów szybkiego startu platformy Azure](https://github.com/Azure/azure-quickstart-templates) w witrynie GitHub, które będą stanowić podstawę w przypadku uruchamiania na nowym szablonie lub dodania do istniejącej.

Szablony Menedżer zasobów można uruchamiać na wiele sposobów. Prawdopodobnie najprostszym sposobem jest po prostu wklejenie ich do Azure Portal. W przypadku wdrożeń eksperymentalnych ta metoda może być bardzo szybka. Mogą być również uruchamiane jako część procesu kompilowania lub wydawania wersji w usłudze Azure DevOps. Istnieją zadania, które będą korzystać z połączeń na platformie Azure w celu uruchamiania szablonów. Zmiany w szablonach Menedżer zasobów są stosowane przyrostowo, co oznacza, że dodanie nowego zasobu wymaga tylko dodania go do szablonu. Narzędzia będą obsługiwać różnicowanie bieżącej grupy zasobów z żądaną grupą zasobów zdefiniowaną w szablonie. Zasoby zostaną następnie utworzone lub zmienione, aby były zgodne z tym, co zostało zdefiniowane w szablonie.  

## <a name="terraform"></a>Terraform

Postrzegana wada Menedżer zasobów szablonów polega na tym, że są one specyficzne dla chmury platformy Azure. Nie ma potrzeby tworzenia aplikacji, które obejmują zasoby z więcej niż jednej chmury, ale w przypadkach, w których działalność biznesowa opiera się na spektakularnych czasowym, koszt obsługi wielu chmur może być wartościowa. W przypadku użycia jednego języka tworzenia szablonów, który może być używany w każdej chmurze, można także zapewnić, że kwalifikacje deweloperów będą znacznie bardziej przenośne.

Istnieje kilka technologii, które wystarczy! Najbardziej dojrzała oferta w tym miejscu jest znana jako [Terraform](https://www.terraform.io/). Usługa Terraform obsługuje każdy główny odtwarzacz w chmurze, taki jak Azure, Google Cloud Platform, AWS i AliCloud, a także obsługuje dziesiątki drobnych odtwarzaczy, takich jak Heroku i DigitalOcean. Zamiast używać formatu JSON jako języka definicji szablonu, wykorzystuje nieco więcej zwięzła YAML.

Przykładowy plik Terraform, który jest taki sam jak poprzedni szablon Menedżer zasobów (Rysunek 11-11) przedstawiono na rysunku 11-12:

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

**Rysunek 11-12** — przykład szablonu Menedżer zasobów

Terraform wykonuje lepsze zadanie zapewniania rozsądnych komunikatów o błędach, gdy nie można wdrożyć zasobu z powodu błędu w szablonie. Jest to obszar, w którym Menedżer zasobów szablony mają pewne ciągłe wyzwania. Istnieje również bardzo przydatne zadanie sprawdzania poprawności, które może być używane w fazie kompilacji do wczesnego przechwytywania błędów szablonów.

Podobnie jak w przypadku szablonów Menedżer zasobów, dostępne są narzędzia wiersza polecenia, których można użyć do wdrożenia szablonów Terraform. Istnieją również zadania utworzone przez społeczność w Azure Pipelines, które mogą weryfikować i stosować szablony Terraform.

W przypadku, gdy szablon Terraform lub Menedżer zasobów wyprowadza interesujące wartości, takie jak parametry połączenia, do nowo utworzonej bazy danych, które mogą być przechwytywane w potoku kompilacji i używane w kolejnych zadaniach.

>[!div class="step-by-step"]
>[Poprzedni](devops.md)
>[Następny](application-bundles.md)
