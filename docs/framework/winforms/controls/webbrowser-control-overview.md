---
title: WebBrowser — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: cc998fd88f3487aa20f6cef73aacb6c07f92c7ad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710098"
---
# <a name="webbrowser-control-overview"></a>WebBrowser — Informacje o formancie
<xref:System.Windows.Forms.WebBrowser> Control oferuje zarządzany otok dla formantu WebBrowser ActiveX. Zarządzana otoka służy do wyświetlania stron sieci Web w aplikacjach Windows Forms klienta. Możesz użyć <xref:System.Windows.Forms.WebBrowser> kontrolki duplikowały funkcji przeglądania programu Internet Explorer lub aplikacji można wyłączyć domyślna funkcjonalność programu Internet Explorer i formant jest używany jako prosty przeglądarki dokumentów HTML. Umożliwia także formantu do dodawania elementów interfejsu użytkownika opartego na DHTML do formularza i ukryć fakt, że są hostowane na platformie <xref:System.Windows.Forms.WebBrowser> kontroli. Takie podejście umożliwia bezproblemowe łączenie formantów sieci Web za pomocą kontrolek Windows Forms w jednej aplikacji.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Często używanych właściwości, metody i zdarzenia  
 <xref:System.Windows.Forms.WebBrowser> Kontrolka ma kilka właściwości, metody i zdarzenia, które można użyć do zaimplementowania kontrolki w programie Internet Explorer. Na przykład, można użyć `Navigate` metody do zaimplementowania pasku adresu i `GoBack`, `GoForward`, `Stop`, i `Refresh` metody służące do implementacji przyciski nawigacji na pasku narzędzi. Może obsługiwać `Navigated` zdarzenie, aby zaktualizować paska adresu z wartością `Url` właściwości i na pasku tytułu z wartością `DocumentTitle` właściwości.  
  
 Jeśli chcesz wygenerować własną zawartość strony w aplikacji, możesz ustawić `DocumentText` właściwości. Jeśli znasz HTML document object model (DOM), również można manipulować zawartością bieżącej strony sieci Web za pośrednictwem `Document` właściwości. Za pomocą tej właściwości można przechowywać i modyfikowania dokumentów w pamięci, zamiast przechodzenia między plikami.  
  
 `Document` Właściwość umożliwia także wywołać metod zaimplementowanych na stronie sieci Web skryptów kodu od kodu aplikacji klienta. Aby uzyskać dostęp do kodu aplikacji klienta, w kodzie obsługi skryptów, należy ustawić `ObjectForScripting` właściwości. Obiekt, który określisz może zostać oceniony przez kod skryptu jako `window.external` obiektu.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> Właściwość|Pobiera obiekt, który zapewnia zarządzany dostęp do kodu HTML document object model (DOM) bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Zdarzenia|Występuje, gdy zakończenie ładowania strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> Właściwość|Pobiera lub ustawia zawartość bieżącej strony sieci Web HTML.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> Właściwość|Pobiera tytuł bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> — Metoda|Powoduje przejście do poprzedniej strony w historii.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> — Metoda|Powoduje przejście do następnej strony w historii.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> — Metoda|Powoduje przejście do określonego adresu URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> Zdarzenia|Występuje przed rozpoczęciem nawigacji, umożliwiając akcji, które zostaną anulowane.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> Właściwość|Pobiera lub ustawia obiekt, który strony sieci Web, kod skryptowy można użyć do komunikacji z aplikacją.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> — Metoda|Drukuje bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> — Metoda|Ponownie ładuje bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> — Metoda|Zatrzymuje bieżący nawigacji i zatrzymuje strony dynamicznej elementów, takich jak dźwięki i animacji.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> Właściwość|Pobiera lub ustawia adres URL bieżącej strony sieci Web. Ustawienie tej właściwości powoduje przejście kontrolki na nowy adres URL.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [Instrukcje: Przejdź do adresu URL za pomocą formantu WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Instrukcje: Drukowanie za pomocą formantu WebBrowser](how-to-print-with-a-webbrowser-control.md)
- [Instrukcje: Dodawanie funkcji przeglądarki sieci Web do aplikacji programu Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Instrukcje: Tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Instrukcje: Implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta](implement-two-way-com-between-dhtml-and-client.md)
- [Zabezpieczenia WebBrowser](webbrowser-security.md)
