---
title: Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 901d0b80a18d2f4d262cc65eb485dcc628bc6a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591862"
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)
Visual Basic umożliwia łatwe do wdrożenia niestandardowe `My` rozszerzeń nazw przy użyciu szablonów programu Visual Studio. Jeśli tworzysz szablon projektu, dla którego Twojej `My` rozszerzenia są integralną częścią nowy typ projektu, po prostu może zawierać niestandardowe `My` kod rozszerzenia w projekcie podczas eksportowania szablonu. Aby uzyskać więcej informacji na temat eksportowania szablonów projektu, zobacz [porady: Tworzenie szablonów projektów](/visualstudio/ide/how-to-create-project-templates).  
  
 Jeśli niestandardowe `My` rozszerzenia znajduje się w pliku kodu pojedynczego, możesz wyeksportować plik jako szablon elementu, który użytkownicy mogą dodawać do dowolnego typu projektu Visual Basic. Następnie możesz dostosować szablon elementu, aby włączyć dodatkowe funkcje i zachowanie dla niestandardowych `My` rozszerzenia w projektach Visual Basic. Te możliwości są następujące:  
  
-   Zezwalanie użytkownikom na zarządzanie niestandardowe `My` rozszerzenia **Moje rozszerzenia** strony projektanta projektu Visual Basic.  
  
-   Automatyczne dodawanie niestandardowe `My` rozszerzenia, gdy odwołanie do określonego zestawu jest dodawany do projektu.  
  
-   Ukrywanie `My` szablon elementu rozszerzenia w **Dodaj element** okna dialogowego, dzięki czemu nie znajduje się na liście elementów projektu.  
  
 W tym temacie omówiono sposób pakiet niestandardowy `My` rozszerzenia jako szablon ukryty element, który można zarządzać za pomocą **Moje rozszerzenia** strony projektanta projektu Visual Basic. Niestandardowa `My` rozszerzenia można również dodać automatycznie podczas dodawania do projektu odwołanie do określonego zestawu.  
  
## <a name="create-a-my-namespace-extension"></a>Utwórz moje rozszerzenie przestrzeni nazw  
 Pierwszym krokiem podczas tworzenia pakietu wdrożeniowego dla niestandardowego `My` rozszerzenia jest utworzenie rozszerzenia jako plik pojedynczy kod. Szczegółowe informacje i wskazówki dotyczące sposobu tworzenia niestandardowego `My` rozszerzenia, zobacz [rozszerzanie My Namespace w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Eksportuj Moje rozszerzenie przestrzeni nazw jako szablon elementu  
 Po utworzeniu pliku kodu, który zawiera Twoje `My` rozszerzenie przestrzeni nazw, możesz wyeksportować plik kodu jako szablon elementu programu Visual Studio. Aby uzyskać instrukcje na temat sposobu eksportowania pliku jako szablon elementu programu Visual Studio, zobacz [porady: Tworzenie szablonów elementów](/visualstudio/ide/how-to-create-item-templates).  
  
> [!NOTE]
>  Jeśli Twoje `My` rozszerzenie przestrzeni nazw ma zależność w określonym zestawie, można dostosować szablon elementu, aby automatycznie zainstalować z `My` rozszerzenia nazw podczas dodawania odwołania do tego zestawu. W związku z tym można wykluczyć odwołanie do zestawu, podczas eksportowania pliku kodu jako szablon elementu programu Visual Studio.  
  
## <a name="customize-the-item-template"></a>Dostosowywanie szablonu elementu  
 Można włączyć można zarządzać za pomocą szablonu elementu **Moje rozszerzenia** strony projektanta projektu Visual Basic. Można również włączyć szablon elementu, który ma zostać dodana automatycznie po dodaniu do projektu odwołanie do określonego zestawu. Aby włączyć te modyfikacje, będzie Dodaj nowy plik o nazwie pliku CustomData szablonu i następnie dodać nowego elementu do pliku XML w pliku .vstemplate.  
  
### <a name="add-the-customdata-file"></a>Dodaj plik CustomData  
 Plik CustomData jest plik tekstowy, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku można ustawić dowolną wartość zrozumiały dla szablonu) i który zawiera kod XML. Kod XML w pliku CustomData nakazuje Visual Basic, aby uwzględnić Twojej `My` rozszerzenia, gdy użytkownicy używają **Moje rozszerzenia** strony projektanta projektu Visual Basic. Możesz opcjonalnie dodać <`AssemblyFullName>` atrybutu CustomData pliku XML. Powoduje to, że Visual Basic, aby automatycznie zainstalować niestandardowe `My` rozszerzenia, gdy odwołanie do określonego zestawu jest dodane do projektu. Można użyć dowolnego edytora tekstu lub edytora XML, aby utworzyć plik CustomData, a następnie dodaj go do szablonu elementu skompresowanego folderu (pliku .zip).  
  
 Na przykład następujący kod XML zawiera zawartość pliku CustomData, który doda element szablonu do folderu Moje rozszerzenia projektu Visual Basic, gdy odwołanie do zestawu Microsoft.VisualBasic.PowerPacks.Vs.dll jest dodane do projektu.  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 Zawiera plik CustomData <`VBMyExtensionTemplate>` element, który ma atrybuty wymienione w poniższej tabeli.  
  
|Atrybut|Opis|  
|---|---|  
|`ID`|Wymagana. Unikatowy identyfikator dla rozszerzenia. Jeśli rozszerzenie o tym identyfikatorze został już dodany do projektu, użytkownik nie będzie monitowany dodać ją ponownie.|  
|`Version`|Wymagana. Numer wersji dla szablonu elementu.|  
|`AssemblyFullName`|Opcjonalna. Nazwa zestawu. Gdy odwołanie do tego zestawu zostanie dodany do projektu, użytkownik będzie monitu o dodanie `My` rozszerzenia na podstawie tego szablonu elementu.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Dodaj \<customdatasignature — > w pliku .vstemplate — element  
 Aby zidentyfikować szablonu elementów programu Visual Studio jako `My` rozszerzenie przestrzeni nazw, należy również zmodyfikować plik .vstemplate szablonu elementu. Należy dodać `<CustomDataSignature>` elementu `<TemplateData>` elementu. `<CustomDataSignature>` Element musi zawierać tekst `Microsoft.VisualBasic.MyExtension`, jak pokazano w poniższym przykładzie.  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Nie można bezpośrednio modyfikować pliki w skompresowanym folderze (pliku .zip). Należy skopiować plik .vstemplate ze skompresowanego folderu, go zmodyfikować i następnie zastąpić plik .vstemplate ze skompresowanego folderu kopii zaktualizowane.  
  
 W poniższym przykładzie pokazano zawartość pliku .vstemplate, który ma `<CustomDataSignature>` elementu dodany.  
  
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
 Aby zainstalować szablon, należy skopiować skompresowanym folderze (pliku .zip) w folderze Szablony elementów Visual Basic (na przykład Moje Documents\Visual Studio 2008\Templates\Item Templates\Visual podstawowe). Alternatywnie możesz opublikować szablon jako plik Instalator programu Visual Studio (.vsi).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie Moje Namespace w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Rozszerzanie modelu aplikacji Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Dostosowywanie, które obiekty są dostępne w My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Strona Moje rozszerzenia, Projektant projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
