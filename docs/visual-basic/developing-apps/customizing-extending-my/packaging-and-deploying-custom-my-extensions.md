---
title: Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014209"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)

Visual Basic zapewnia łatwy sposób można wdrażać niestandardowe `My` rozszerzenia nazw przy użyciu szablonów programu Visual Studio. Jeśli tworzysz szablon projektu, dla którego Twoja `My` rozszerzenia są integralną częścią nowy typ projektu, możesz po prostu dołączyć niestandardowe `My` rozszerzenia kodu z projektem podczas eksportowania szablonu. Aby uzyskać więcej informacji na temat eksportowania szablonów projektu, zobacz [jak: Tworzenie szablonów projektów](/visualstudio/ide/how-to-create-project-templates).

Jeśli niestandardowe `My` rozszerzenia znajduje się w pliku pojedynczego kodu, możesz wyeksportować plik jako szablon elementu, który użytkownicy mogą dodawać do dowolnego typu projektu języka Visual Basic. Następnie można dostosować szablon elementu, aby włączyć dodatkowe funkcje i działanie dla niestandardowych `My` rozszerzeń w projekcie Visual Basic. Te możliwości są następujące:

- Zezwalanie użytkownikom na zarządzanie niestandardowe `My` rozszerzenie z **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic.

- Automatyczne dodawanie niestandardowych `My` rozszerzenia, gdy odwołanie do określonego zestawu został dodany do projektu.

- Ukrywanie `My` szablon elementu rozszerzenia w **elementu Dodawanie** okno dialogowe, tak aby nie znajduje się na liście elementów projektu.

W tym temacie omówiono sposób pakowania niestandardowego `My` rozszerzenia jako szablon ukryty element, który można zarządzać przy użyciu **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic. Niestandardowy `My` rozszerzenia mogą być również dodawane automatycznie po dodaniu do projektu odwołanie do określonego zestawu.

## <a name="create-a-my-namespace-extension"></a>Utwórz moje rozszerzenie przestrzeni nazw

Pierwszym krokiem w tworzeniu pakietu wdrożeniowego dla niestandardowego `My` rozszerzenia polega na utworzeniu rozszerzenia jako plik pojedynczego kodu. Aby uzyskać szczegółowe informacje i wskazówki dotyczące sposobu tworzenia niestandardowego `My` rozszerzenia, zobacz [rozszerzanie My Namespace w języku Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Eksportuj Moje rozszerzenie przestrzeni nazw jako szablon elementu

Po utworzeniu pliku z kodem, który zawiera Twoje `My` rozszerzenie przestrzeni nazw, możesz wyeksportować plik kodu jako szablonu elementu programu Visual Studio. Aby uzyskać instrukcje dotyczące sposobu eksportowania pliku jako szablon elementu programu Visual Studio, zobacz [jak: Tworzenie szablonów elementu](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Jeśli Twoje `My` rozszerzenie przestrzeni nazw ma zależność od określonego zestawu, można dostosować szablon elementu, aby automatycznie zainstalować swoje `My` rozszerzenie przestrzeni nazw, po dodaniu odwołania do tego zestawu. Co w efekcie można wykluczyć odwołanie do zestawu, eksportując plik kodu jako szablonu elementu programu Visual Studio.

## <a name="customize-the-item-template"></a>Dostosowywanie szablonu elementu

Można włączyć usługi można zarządzać za pomocą szablonu elementu **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic. Można również włączyć szablon elementu, który ma zostać dodana automatycznie, gdy odwołanie do określonego zestawu zostanie dodany do projektu. Aby włączyć te modyfikacje, będzie Dodaj nowy plik o nazwie pliku CustomData do szablonu, a następnie dodaj nowy element do pliku XML w pliku .vstemplate.

### <a name="add-the-customdata-file"></a>Dodaj plik CustomData

Plik CustomData jest plik tekstowy, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku można ustawić dowolną wartość zrozumiałe dla szablonu) i która zawiera kod XML. Kod XML w pliku CustomData powoduje, że Visual Basic, aby dołączyć swoje `My` rozszerzenia, gdy użytkownicy korzystają **Moje rozszerzenia** strony w Projektancie projektu języka Visual Basic. Możesz opcjonalnie dodać <`AssemblyFullName>` atrybutu CustomData pliku XML. To powoduje, że Visual Basic, aby automatycznie zainstalować niestandardowe `My` rozszerzenia, gdy odwołanie do konkretnego zestawu jest dodawany do projektu. Można użyć dowolnego edytora tekstu lub edytorze XML, aby utworzyć plik CustomData, a następnie dodaj go do szablonu elementu skompresowany folder (plik zip).

Na przykład, następujący kody XML pokazuje zawartość pliku CustomData, który doda element szablonu do folderu rozszerzeń mój projekt Visual Basic, gdy odwołanie do zestawu Microsoft.VisualBasic.PowerPacks.Vs.dll zostanie dodany do projektu.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Zawiera plik CustomData <`VBMyExtensionTemplate>` element, który zawiera atrybuty wymienione w poniższej tabeli.

|Atrybut|Opis|
|---|---|
|`ID`|Wymagana. Unikatowy identyfikator dla rozszerzenia. Jeśli rozszerzenie, które mają ten identyfikator został już dodany do projektu, użytkownik nie będzie monitowany ponownie dodać.|
|`Version`|Wymagana. Numer wersji szablonu elementu.|
|`AssemblyFullName`|Opcjonalna. Nazwa zestawu. Po dodaniu do projektu odwołanie do tego zestawu użytkownika zostanie wyświetlony monit Dodaj `My` rozszerzenia za pomocą tego szablonu elementu.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Dodaj \<CustomDataSignature > element pliku .vstemplate

Aby zidentyfikować szablonu elementu programu Visual Studio jako `My` rozszerzenie przestrzeni nazw, należy również zmodyfikować plik .vstemplate szablonu elementu. Należy dodać `<CustomDataSignature>` elementu `<TemplateData>` elementu. `<CustomDataSignature>` Element musi zawierać tekst `Microsoft.VisualBasic.MyExtension`, jak pokazano w poniższym przykładzie.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Nie można bezpośrednio modyfikować pliki w skompresowanym folderze (pliku zip). Należy skopiować plik .vstemplate ze skompresowanego folderu, go zmodyfikować, a następnie zastąp plik .vstemplate w skompresowanym folderze kopią zaktualizowane.

W poniższym przykładzie pokazano zawartość pliku .vstemplate, który ma `<CustomDataSignature>` dodany element.

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>Zainstaluj szablonu

Aby zainstalować tego szablonu, należy skopiować skompresowany folder (*zip* plików) do folderu Szablony elementów Visual Basic. Domyślnie, szablonów elementów użytkownika znajdują się w *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual Basic*. Alternatywnie można opublikować szablon jako Instalator programu Visual Studio (*.vsi*) pliku.

## <a name="see-also"></a>Zobacz także

- [Rozszerzanie mojej Namespace w języku Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
