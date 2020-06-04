---
title: Obiekty
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: e927f69b7606866a0a9e8eadd59270f51ffc5e2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414222"
---
# <a name="objects-visual-basic"></a>Obiekty (Visual Basic)
Ten temat zawiera linki do innych tematów, które dokumentują Visual Basic obiekty czasu wykonywania i zawierają tabele ich procedur, właściwości i zdarzeń członków.  
  
## <a name="visual-basic-run-time-objects"></a>Visual Basic obiektów czasu wykonywania  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Zapewnia wygodny sposób wyświetlania powiązanej grupy elementów jako pojedynczego obiektu.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Zawiera informacje o błędach czasu wykonywania.|  
|`My.Application`Obiekt składa się z następujących klas:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>zapewnia składowe, które są dostępne we wszystkich projektach.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>zapewnia składowe dostępne w aplikacjach Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>zapewnia składowe dostępne w aplikacjach konsolowych.|Dostarcza dane, które są skojarzone tylko z bieżącą aplikacją lub biblioteką DLL. Informacje na poziomie systemu nie mogą być zmieniane za pomocą programu `My.Application` .<br /><br /> Niektóre elementy członkowskie są dostępne tylko dla aplikacji Windows Forms lub konsoli programu.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Zawiera właściwości służące do uzyskiwania informacji o aplikacji, takich jak numer wersji, opis, ładowane zestawy itd.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Zawiera właściwości i metody zapisu informacji o zdarzeniu i wyjątku w detektorach dzienników aplikacji.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Zawiera właściwości służące do manipulowania składnikami komputerów, takimi jak dźwięk, zegar, klawiatura, system plików i tak dalej.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Zapewnia metody odtwarzania dźwięków.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Zapewnia metody manipulowania schowkiem.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Zapewnia właściwości do uzyskiwania dostępu do bieżącego czasu lokalnego i uniwersalnego czasu koordynowanego (równoważnego czasowi Greenwich) z zegara systemowego.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Zawiera właściwości i metody pracy z dyskami, plikami i katalogami.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Udostępnia właściwości do uzyskiwania dostępu do najczęściej występujących katalogów.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Zawiera właściwości służące do uzyskiwania informacji o pamięci komputera, załadowanych zestawach, nazwie i systemie operacyjnym.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Zapewnia właściwości do uzyskiwania dostępu do bieżącego stanu klawiatury, takie jak klucze są aktualnie naciśnięte i zapewnia metodę wysyłania naciśnięć klawiszy do aktywnego okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Zawiera właściwości służące do uzyskiwania informacji o formacie i konfiguracji myszy, która jest zainstalowana na komputerze lokalnym.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Zawiera właściwości, zdarzenie i metody umożliwiające współdziałanie z siecią, do której komputer jest połączony.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Zawiera właściwość i metodę uzyskiwania dostępu do portów szeregowych komputera.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Zawiera właściwości i metody manipulowania rejestrem.|  
|[My.Forms — Obiekt](my-forms-object.md)|Zawiera właściwości umożliwiające dostęp do wystąpienia każdego formularza systemu Windows zadeklarowanego w bieżącym projekcie.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Zawiera właściwości i metody zapisywania informacji o zdarzeniach i wyjątkach w detektorach dzienników aplikacji dla aplikacji sieci Web.|  
|[My.Request — Obiekt](my-request-object.md)|Pobiera <xref:System.Web.HttpRequest> obiekt dla żądanej strony. `My.Request`Obiekt zawiera informacje o bieżącym ŻĄDANIU http.<br /><br /> `My.Request`Obiekt jest dostępny tylko dla aplikacji ASP.NET.|  
|[My.Resources — Obiekt](my-resources-object.md)|Udostępnia właściwości i klasy do uzyskiwania dostępu do zasobów aplikacji.|  
|[My.Response — Obiekt](my-response-object.md)|Pobiera <xref:System.Web.HttpResponse> obiekt, który jest skojarzony z <xref:System.Web.UI.Page> . Ten obiekt umożliwia wysyłanie danych odpowiedzi HTTP do klienta programu i zawiera informacje o tej odpowiedzi.<br /><br /> `My.Response`Obiekt jest dostępny tylko dla aplikacji ASP.NET.|  
|[My.Settings — Obiekt](my-settings-object.md)|Zawiera właściwości i metody uzyskiwania dostępu do ustawień aplikacji.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Zapewnia dostęp do informacji o bieżącym użytkowniku.|  
|[My.WebServices — Obiekt](my-webservices-object.md)|Zawiera właściwości służące do tworzenia i uzyskiwania dostępu do pojedynczego wystąpienia każdej usługi sieci Web, do której odwołuje się bieżący projekt.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Zapewnia metody i właściwości do analizowania strukturalnych plików tekstowych.|  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka Visual Basic](../index.md)
