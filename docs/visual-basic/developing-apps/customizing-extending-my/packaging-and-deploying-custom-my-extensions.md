---
title: Pakowanie i wdrażanie niestandardowych rozszerzeń my
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330259"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Pakowanie i wdrażanie niestandardowych rozszerzeń my (Visual Basic)

Visual Basic zapewnia łatwy sposób wdrażania niestandardowych `My` rozszerzeń przestrzeni nazw za pomocą szablonów programu Visual Studio. Jeśli tworzysz szablon projektu, dla którego `My` rozszerzenia są integralną częścią nowego typu projektu, możesz po prostu dołączyć niestandardowy `My` kod rozszerzenia do projektu podczas eksportowania szablonu. Aby uzyskać więcej informacji na temat eksportowania szablonów projektów, zobacz [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).

Jeśli niestandardowe `My` rozszerzenie znajduje się w pojedynczym pliku kodu, można wyeksportować plik jako szablon elementu, który użytkownicy mogą dodać do dowolnego typu Visual Basic projektu. Następnie można dostosować szablon elementu, aby umożliwić dodatkowe możliwości i zachowanie dla niestandardowego `My` rozszerzenia w projekcie Visual Basic. Dostępne są następujące możliwości:

- Umożliwienie użytkownikom zarządzania rozszerzeniami `My` niestandardowymi na stronie **Moje rozszerzenia** w projektancie projektu Visual Basic.

- Automatyczne dodanie niestandardowego `My` rozszerzenia, gdy odwołanie do określonego zestawu zostanie dodane do projektu.

- Ukrywanie szablonu `My` elementu rozszerzenia w oknie dialogowym **Dodaj element** , tak aby nie był on uwzględniony na liście elementów projektu.

W tym temacie omówiono sposób pakowania rozszerzenia niestandardowego `My` jako szablonu ukrytego elementu, który można zarządzać z poziomu strony **Moje rozszerzenia** w projektancie projektu Visual Basic. Rozszerzenie niestandardowe `My` można również dodać automatycznie, gdy odwołanie do określonego zestawu zostanie dodane do projektu.

## <a name="create-a-my-namespace-extension"></a>Tworzenie rozszerzenia my Namespace

Pierwszym krokiem tworzenia pakietu wdrożeniowego dla rozszerzenia niestandardowego `My` jest utworzenie rozszerzenia jako pojedynczego pliku kodu. Aby uzyskać szczegółowe informacje i wskazówki dotyczące sposobu tworzenia rozszerzenia `My` niestandardowego, zobacz [rozszerzanie przestrzeni nazw my w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Eksportowanie rozszerzenia my Namespace jako szablonu elementu

Po utworzeniu pliku z kodem, który zawiera rozszerzenie `My` przestrzeni nazw, można wyeksportować plik kodu jako szablon elementu programu Visual Studio. Aby uzyskać instrukcje dotyczące sposobu eksportowania pliku jako szablonu elementu programu Visual Studio, zobacz [How to: Create Item templates](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Jeśli rozszerzenie `My` przestrzeni nazw ma zależność od określonego zestawu, można dostosować szablon elementu, aby automatycznie zainstalować rozszerzenie `My` przestrzeni nazw po dodaniu odwołania do tego zestawu. W związku z tym należy wykluczyć to odwołanie do zestawu podczas eksportowania pliku kodu jako szablonu elementu programu Visual Studio.

## <a name="customize-the-item-template"></a>Dostosuj szablon elementu

Szablon elementu można włączyć jako zarządzany na stronie **Moje rozszerzenia** projektanta projektu Visual Basic. Można również włączyć automatyczne Dodawanie szablonu elementu, gdy odwołanie do określonego zestawu zostanie dodane do projektu. Aby włączyć te dostosowania, należy dodać nowy plik o nazwie plik CustomData, do szablonu, a następnie dodać nowy element do pliku XML w plik. vstemplate.

### <a name="add-the-customdata-file"></a>Dodaj plik CustomData

Plik CustomData jest plikiem tekstowym, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku może być ustawiona na dowolną wartość znaczącą dla szablonu), która zawiera kod XML. KOD XML w pliku CustomData instruuje Visual Basic, aby dołączać Twoje `My` rozszerzenie, gdy użytkownicy korzystają z strony **Moje rozszerzenia** projektanta projektu Visual Basic. Opcjonalnie możesz dodać atrybut <`AssemblyFullName>` do pliku XML CustomData. Powoduje to Visual Basic automatyczne zainstalowanie niestandardowego `My` rozszerzenia, gdy odwołanie do określonego zestawu zostanie dodane do projektu. Możesz użyć dowolnego edytora tekstu lub edytora XML, aby utworzyć plik CustomData, a następnie dodać go do skompresowanego folderu szablonu elementu (plik. zip).

Na przykład poniższy kod XML przedstawia zawartość pliku CustomData, który doda element szablonu do folderu Moje rozszerzenia projektu Visual Basic, gdy odwołanie do zestawu Microsoft. VisualBasic. PowerPacks. vs. dll zostanie dodane do projektu.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Plik CustomData zawiera element <`VBMyExtensionTemplate>` , który zawiera atrybuty wymienione w poniższej tabeli.

|Atrybut|Opis|
|---|---|
|`ID`|Wymagany. Unikatowy identyfikator rozszerzenia. Jeśli rozszerzenie, które ma ten identyfikator, zostało już dodane do projektu, użytkownik nie będzie monitowany o ponowne dodanie go.|
|`Version`|Wymagany. Numer wersji szablonu elementu.|
|`AssemblyFullName`|Element opcjonalny. Nazwa zestawu. Gdy odwołanie do tego zestawu zostanie dodane do projektu, użytkownik zostanie poproszony o dodanie `My` rozszerzenia z tego szablonu elementu.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Dodaj element \<> CustomDataSignature do pliku vstemplate

Aby zidentyfikować szablon elementu programu Visual Studio jako rozszerzenie `My` przestrzeni nazw, należy również zmodyfikować plik vstemplate szablonu elementu. Należy dodać `<CustomDataSignature>` element do `<TemplateData>` elementu. `<CustomDataSignature>` Element musi zawierać tekst `Microsoft.VisualBasic.MyExtension`, jak pokazano w poniższym przykładzie.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Nie można bezpośrednio modyfikować plików w skompresowanym folderze (pliku. zip). Należy skopiować plik. vstemplate z folderu skompresowanego, zmodyfikować go, a następnie zastąpić plik. vstemplate w folderze skompresowanym przy użyciu zaktualizowanej kopii.

Poniższy przykład pokazuje zawartość pliku. vstemplate, który ma dodany `<CustomDataSignature>` element.

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

## <a name="install-the-template"></a>Instalowanie szablonu

Aby zainstalować szablon, można skopiować skompresowany folder (plik*zip* ) do folderu szablonów elementów Visual Basic. Domyślnie szablony elementów użytkownika znajdują się w programie *%USERPROFILE%\Documents\Visual Studio \<w\>wersji \Templates\ItemTemplates\Visual Basic*. Alternatywnie można opublikować szablon jako plik Instalator programu Visual Studio (*. VSI*).

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie przestrzeni nazw My w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
