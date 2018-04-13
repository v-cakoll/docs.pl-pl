---
title: Obiekty (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61c0967521acda8ac3bf8147b817afcf4ca51165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="objects-visual-basic"></a>Obiekty (Visual Basic)
Ten temat zawiera linki do innych tematów dokumentu środowiska wykonawczego Visual Basic obiekty i zawiera tabele ich procedur — członek, właściwości i zdarzeń.  
  
## <a name="visual-basic-run-time-objects"></a>Obiekty środowiska wykonawczego Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Zapewnia to wygodny sposób Zobacz pokrewne grupę elementów jako pojedynczego obiektu.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Zawiera informacje na temat błędów czasu wykonywania.|  
|`My.Application` Obiekt składa się z następujących klas:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>zawiera elementy członkowskie, które są dostępne we wszystkich projektach.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>zapewnia to członkom dostępne w aplikacjach formularzy systemu Windows.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>zapewnia to członkom dostępne w aplikacji konsoli.|Zapewnia dane, które są skojarzone tylko z bieżącej aplikacji lub DLL. Żadne informacje poziom systemu można zmienić z `My.Application`.<br /><br /> Niektóre elementy są dostępne tylko w przypadku formularzy systemu Windows lub aplikacji konsoli.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Udostępnia właściwości do pobierania informacji o aplikacji, takich jak numer wersji, opis, załadowanych zestawów i tak dalej.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Udostępnia właściwości i metody mogła zapisać informacji zdarzeń i wyjątków do odbiorniki dzienników aplikacji.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Udostępnia właściwości do manipulowania komputera składniki, takie jak audio, zegara, klawiatura, system plików i tak dalej.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Udostępnia metody dla odtwarzanie dźwięków.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Udostępnia metody do manipulowania Schowka.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Dostarcza właściwości, aby uzyskać dostęp do bieżący czas lokalny i uniwersalny czas koordynowany (odpowiednik czas uniwersalny Greenwich) z zegara systemowego.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Udostępnia właściwości i metody do pracy z dysków, plików i katalogów.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Zawiera właściwości do uzyskiwania dostępu do często odwołuje się do katalogów.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Udostępnia właściwości do pobierania informacji o pamięci, załadowanych zestawów, nazwy i systemu operacyjnego komputera.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Dostarcza właściwości, aby uzyskać dostęp do bieżącego stanu klawiatury, takie jak co klucze są obecnie naciśnięty i udostępnia metodę Wyślij naciśnięcia klawiszy do aktywnego okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Udostępnia właściwości do pobierania informacji o formacie i konfiguracji myszy, który jest zainstalowany na komputerze lokalnym.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Udostępnia właściwości, zdarzeń i metody interakcji z sieci, do której komputer jest połączony.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Udostępnia właściwości i metody do uzyskiwania dostępu do portów szeregowych komputera.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Udostępnia właściwości i metody w rejestrze.|  
|[My.Forms — obiekt](../../../visual-basic/language-reference/objects/my-forms-object.md)|Zawiera właściwości do uzyskiwania dostępu do wystąpienia każdego formularza systemu Windows jest zadeklarowana w bieżącym projekcie.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Udostępnia właściwości i metody dla zapisywania informacji o zdarzeń i wyjątków na odbiorniki dzienników aplikacji dla aplikacji sieci Web.|  
|[My.Request — obiekt](../../../visual-basic/language-reference/objects/my-request-object.md)|Pobiera <xref:System.Web.HttpRequest> obiektu dla żądanej strony. `My.Request` Zawiera informacje o bieżącym żądaniu HTTP.<br /><br /> `My.Request` Jest dostępna tylko dla obiekt [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.|  
|[My.resources — obiekt](../../../visual-basic/language-reference/objects/my-resources-object.md)|Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.|  
|[My.Response — obiekt](../../../visual-basic/language-reference/objects/my-response-object.md)|Pobiera <xref:System.Web.HttpResponse> obiektu, z którym skojarzony jest <xref:System.Web.UI.Page>. Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta i zawiera informacje o tej odpowiedzi.<br /><br /> `My.Response` Jest dostępna tylko dla obiekt [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikacji.|  
|[My.Settings — obiekt](../../../visual-basic/language-reference/objects/my-settings-object.md)|Udostępnia właściwości i metod dostępu do ustawień aplikacji.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Zapewnia dostęp do informacji dotyczących bieżącego użytkownika.|  
|[My.WebServices — obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Udostępnia właściwości umożliwiające tworzenie i uzyskiwanie dostępu do jednego wystąpienia każdej usługi sieci Web, do którego odwołuje się w bieżącym projekcie.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Udostępnia metody i właściwości dla analizowanie tekstu w strukturze plików.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../../visual-basic/index.md)
