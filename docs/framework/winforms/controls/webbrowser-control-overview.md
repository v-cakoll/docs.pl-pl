---
title: WebBrowser — Informacje o formancie
description: Dowiedz się, jak za pomocą kontrolki WebBrowser bezproblemowo łączyć formanty sieci Web z kontrolkami Windows Forms w pojedynczej aplikacji.
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325746"
---
# <a name="webbrowser-control-overview"></a>WebBrowser — Informacje o formancie
<xref:System.Windows.Forms.WebBrowser>Formant zawiera zarządzaną otokę dla kontrolki ActiveX WebBrowser. Otoka zarządzana umożliwia wyświetlanie stron sieci Web w aplikacjach klienckich Windows Forms. Możesz użyć <xref:System.Windows.Forms.WebBrowser> kontrolki do duplikowania funkcji przeglądania sieci Web w programie Internet Explorer w aplikacji lub można wyłączyć domyślną funkcjonalność programu Internet Explorer i użyć kontrolki jako prostej przeglądarki dokumentów HTML. Można również użyć kontrolki do dodania do formularza elementów interfejsu użytkownika opartych na protokole DHTML i ukrycia faktu, że są one hostowane w <xref:System.Windows.Forms.WebBrowser> formancie. Takie podejście umożliwia bezproblemowe łączenie formantów sieci Web z kontrolkami Windows Forms w pojedynczej aplikacji.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Często używane właściwości, metody i zdarzenia  
 <xref:System.Windows.Forms.WebBrowser>Kontrolka zawiera kilka właściwości, metod i zdarzeń, których można użyć do implementowania formantów znalezionych w programie Internet Explorer. Na przykład można użyć `Navigate` metody do zaimplementowania paska adresu oraz `GoBack` `GoForward` metod,, `Stop` i, `Refresh` Aby zaimplementować przyciski nawigacji na pasku narzędzi. Możesz obsłużyć `Navigated` zdarzenie, aby zaktualizować pasek adresu przy użyciu wartości `Url` właściwości i paska tytułu z wartością `DocumentTitle` właściwości.  
  
 Jeśli chcesz wygenerować własną zawartość strony w aplikacji, możesz ustawić `DocumentText` Właściwość. Jeśli wiesz już, jak dokument HTML Document Object Model (DOM), możesz również manipulować zawartością bieżącej strony sieci Web za pomocą `Document` właściwości. Za pomocą tej właściwości można przechowywać i modyfikować dokumenty w pamięci zamiast nawigować między plikami.  
  
 `Document`Właściwość umożliwia również wywoływanie metod zaimplementowanych w kodzie skryptów strony sieci Web z kodu aplikacji klienta. Aby uzyskać dostęp do kodu aplikacji klienckiej z kodu skryptu, należy ustawić `ObjectForScripting` Właściwość. Do określonego obiektu można uzyskać dostęp za pomocą kodu skryptu jako `window.external` obiektu.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A>wartość|Pobiera obiekt, który zapewnia zarządzany dostęp do modelu DOM (Document Object Model) bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>wydarzen|Występuje po zakończeniu ładowania strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A>wartość|Pobiera lub ustawia zawartość HTML bieżącej strony sieci Web.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>wartość|Pobiera tytuł bieżącej strony sieci Web.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Przechodzi do poprzedniej strony w historii.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Przechodzi do następnej strony w historii.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Przechodzi do podanego adresu URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>wydarzen|Występuje przed rozpoczęciem nawigacji, co umożliwia anulowanie akcji.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>wartość|Pobiera lub ustawia obiekt, który może być używany przez skrypt strony sieci Web do komunikowania się z Twoją aplikacją.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Print%2A>|Drukuje bieżącą stronę sieci Web.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Ponownie ładuje bieżącą stronę sieci Web.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Wstrzymuje bieżącą nawigację i zatrzymuje dynamiczne elementy strony, takie jak dźwięki i animacje.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A>wartość|Pobiera lub ustawia adres URL bieżącej strony sieci Web. Ustawienie tej właściwości powoduje przejście do nowego adresu URL.|  
  
## <a name="see-also"></a>Zobacz też

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
- [Porady: nawigowanie do adresu URL za pomocą formantu WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Instrukcje: drukowanie za pomocą kontrolki WebBrowser](how-to-print-with-a-webbrowser-control.md)
- [Porady: dodawanie funkcji przeglądarki sieci Web do aplikacji Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Instrukcje: tworzenie przeglądarki dokumentów HTML w aplikacji Windows Forms](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Instrukcje: implementowanie dwukierunkowej komunikacji między kodem DHTML i kodem aplikacji klienta](implement-two-way-com-between-dhtml-and-client.md)
- [Zabezpieczenia WebBrowser](webbrowser-security.md)
