---
title: Obiekty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 9e0b133147fa01b15104b9050cd9067079300e3e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486847"
---
# <a name="objects-visual-basic"></a>Obiekty (Visual Basic)
Ten temat zawiera łącza do innych tematów tego dokumentu, środowiska wykonawczego języka Visual Basic obiektów i znajdują się tabele, ich procedur elementu członkowskiego, właściwości i zdarzenia.  
  
## <a name="visual-basic-run-time-objects"></a>Obiekty środowiska wykonawczego Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Zapewnia wygodny sposób, aby wyświetlić powiązane grupy elementów jako pojedynczy obiekt.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Zawiera informacje na temat błędów czasu wykonywania.|  
|`My.Application` Obiekt składa się z następujących klas:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> zawiera elementy członkowskie, które są dostępne we wszystkich projektach.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> zawiera elementy członkowskie dostępne w aplikacjach Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> zawiera elementy członkowskie dostępne w aplikacji konsoli.|Zapewnia dane, które są skojarzone tylko z bieżącej aplikacji lub biblioteki DLL. Brak informacji o poziomie systemu, może się zmienić z `My.Application`.<br /><br /> Niektóre składowe są dostępne tylko w przypadku formularzy Windows lub aplikacji konsoli.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Udostępnia właściwości w celu uzyskania informacji o aplikacji, takich jak numer wersji, opis, załadowanych zestawów i tak dalej.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Udostępnia właściwości i metody w celu zapisywania zdarzeń i wyjątków informacji odbiorniki logu aplikacji.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Udostępnia właściwości do manipulowania komputera składniki, takie jak audio, zegara, klawiatura, system plików i tak dalej.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Udostępnia metody dla odtwarzanie dźwięków.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Udostępnia metody do manipulowania Schowka.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Udostępnia właściwości do uzyskiwania dostępu do bieżącym czasem lokalnym i uniwersalny czas koordynowany (odpowiednik czas uniwersalny Greenwich) z zegarem systemowym.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Udostępnia właściwości i metody do pracy z stacje, plików i katalogów.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Udostępnia właściwości umożliwiające dostęp do często katalogi, do których odwołuje się.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Udostępnia właściwości w celu uzyskania informacji na temat pamięci, załadowanych zestawów, nazwa i systemu operacyjnego komputera.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Udostępnia właściwości do uzyskiwania dostępu do bieżącego stanu klawiatury, takie jak co klucze są obecnie naciśnięte i udostępnia metodę Wyślij naciśnięcia klawiszy do aktywnego okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Udostępnia właściwości w celu uzyskania informacji na temat formatu i konfiguracji myszy, który jest zainstalowany na komputerze lokalnym.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Udostępnia właściwości, zdarzeń i metod do interakcji z sieci, do której komputer jest połączony.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Udostępnia właściwości i metody do uzyskiwania dostępu do portów szeregowych na komputerze.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Udostępnia właściwości i metody do manipulowania w rejestrze.|  
|[My.Forms, obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)|Zawiera właściwości do uzyskiwania dostępu do wystąpienia każdego formularza Windows zadeklarowana w bieżącym projekcie.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Udostępnia właściwości i metody do zapisywania informacji zdarzeń i wyjątków aplikacji odbiorniki logu dla aplikacji sieci Web.|  
|[My.Request, obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)|Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony. `My.Request` Obiekt zawiera informacje o bieżącym żądaniu HTTP.<br /><br /> `My.Request` Obiekt jest dostępny tylko w przypadku [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.|  
|[My.Resources, obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md)|Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.|  
|[My.Response, obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)|Pobiera <xref:System.Web.HttpResponse> obiekt, który jest skojarzony z <xref:System.Web.UI.Page>. Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje dotyczące tej odpowiedzi.<br /><br /> `My.Response` Obiekt jest dostępny tylko w przypadku [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.|  
|[My.Settings, obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md)|Udostępnia właściwości i metod dostępu do ustawień aplikacji.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Zapewnia dostęp do informacji o bieżącym użytkowniku.|  
|[My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Udostępnia właściwości do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia każdą usługę sieci Web, która odwołuje się do bieżącego projektu.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Udostępnia metody i właściwości do analizowania tekstu ze strukturą plików.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../../visual-basic/index.md)
