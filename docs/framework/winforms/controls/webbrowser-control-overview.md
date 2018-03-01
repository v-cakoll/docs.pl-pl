---
title: "WebBrowser — Informacje o formancie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2c1ed93769cc91d9622a86ea2d894cea57f5bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-control-overview"></a>WebBrowser — Informacje o formancie
<xref:System.Windows.Forms.WebBrowser> Kontrola zapewnia zarządzany otok dla formantu WebBrowser ActiveX. Zarządzany otok umożliwia wyświetlanie strony sieci Web w aplikacjach formularzy systemu Windows klienta. Można użyć <xref:System.Windows.Forms.WebBrowser> formantu powielają funkcjonalność przeglądania sieci Web programu Internet Explorer w aplikacji lub można wyłączyć domyślna funkcjonalność programu Internet Explorer i używać kontrolki jako proste przeglądarki dokumentów HTML. Umożliwia także formantu dodawanie do formularza elementów interfejsu użytkownika opartego na DHTML i Ukryj fakt, że są one hostowane w <xref:System.Windows.Forms.WebBrowser> formantu. To rozwiązanie umożliwia bezproblemowe łączenie formantów formanty formularzy systemu Windows w jednej aplikacji sieci Web.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Często używane właściwości, metod i zdarzeń  
 <xref:System.Windows.Forms.WebBrowser> Formant ma kilka właściwości, metod i zdarzeń, które można zaimplementować kontrolki w programie Internet Explorer. Na przykład można użyć `Navigate` metody do zaimplementowania w pasku adresu i `GoBack`, `GoForward`, `Stop`, i `Refresh` metody służące do implementacji przycisków nawigacji na pasku narzędzi. Może obsłużyć `Navigated` zdarzeń do aktualizacji paska adresu z wartością `Url` właściwości i na pasku tytułu z wartością `DocumentTitle` właściwości.  
  
 Jeśli chcesz wygenerować własną zawartość strony w aplikacji, możesz ustawić `DocumentText` właściwości. Jeśli znasz modelu obiektu dokumentu HTML (DOM), można również manipulować zawartością bieżącej strony sieci Web za pośrednictwem `Document` właściwości. Z tą właściwością można przechowywać i modyfikowania dokumentów w pamięci zamiast nawigowanie między plikami.  
  
 `Document` Właściwości umożliwia także wywoływać metod w strony sieci Web skryptów kodu w kodzie aplikacji klienta. Aby uzyskać dostęp do kodu aplikacji klienta w kodzie skryptu, ustaw `ObjectForScripting` właściwości. Obiekt, który określisz można uzyskać, sprawdzając kod skryptu jako `window.external` obiektu.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A>Właściwość|Pobiera obiekt, który udostępnia zarządzany dostęp do HTML document object model (DOM) bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>zdarzenia|Występuje, gdy strona sieci Web zakończeniu ładowania.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A>Właściwość|Pobiera lub ustawia HTML zawartości bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>Właściwość|Pobiera tytuł bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A>— Metoda|Powoduje przejście do poprzedniej strony w historii.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A>— Metoda|Przechodzi do następnej strony w historii.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A>— Metoda|Przechodzi do podanego adresu URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>zdarzenia|Występuje przed rozpoczęciem nawigacji, włączanie Akcja do anulowania.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>Właściwość|Pobiera lub ustawia obiekt, który kod skryptowy strony sieci Web można użyć do komunikacji z aplikacją.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A>— Metoda|Drukuje bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A>— Metoda|Ponownie ładuje bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A>— Metoda|Zatrzymanie bieżącej nawigacji i zatrzymuje strony dynamicznej elementów, takich jak dźwięki i animacji.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A>Właściwość|Pobiera lub ustawia adres URL bieżącej strony sieci Web. Ustawienie tej właściwości przechodzi formant do nowego adresu URL.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [Instrukcje: nawigowanie do adresu URL za pomocą kontrolki WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Instrukcje: drukowanie za pomocą kontrolki WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [Instrukcje: dodawanie funkcji przeglądarki internetowej do aplikacji Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [Instrukcje: tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [Zabezpieczenia WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)
