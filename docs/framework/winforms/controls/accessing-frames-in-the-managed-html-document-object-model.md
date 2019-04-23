---
title: Uzyskiwanie dostępu do ramek w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: 9b2719ca000ab86b9ca40f9e78af46cbf598d16e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337633"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Uzyskiwanie dostępu do ramek w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Niektóre dokumenty HTML składają się z *ramek*, lub windows, które mogą pomieścić własnych unikatowych dokumentów HTML. Przy użyciu klatek można łatwo tworzyć strony HTML, w których statyczne, takie jak pasek nawigacyjny pozostały jedną lub kilka części strony, podczas gdy inne ramki stale zmienić jego zawartość.  
  
 Autorzy utworzyć ramki w jeden z dwóch sposobów:  
  
-   Za pomocą `FRAMESET` i `FRAME` tagi, które tworzą stały systemu windows.  
  
 —lub—  
  
-   Za pomocą `IFRAME` znacznik, który tworzy okno przestawne, które może być przeniesiony w czasie wykonywania.  
  
1. Ponieważ ramki zawierają dokumentów HTML, są one reprezentowane w modelu DOM (Document Object) jako elementy okna i elementy ramki.  
  
2. Jeśli uzyskujesz dostęp do `FRAME` lub `IFRAME` tagu za pomocą klatek zbiór <xref:System.Windows.Forms.HtmlWindow>, pobierają elementu okna odpowiadającego ramki. Ta pozycja reprezentuje wszystkie ramki właściwości dynamicznych, takich jak bieżący adres URL, dokumentów i rozmiaru.  
  
3. Jeśli uzyskujesz dostęp do `FRAME` lub `IFRAME` tagu za pomocą <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> właściwość <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> kolekcji lub metody takie jak <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> lub <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, pobierają elementu ramki. Reprezentuje statycznej właściwości ramki, w tym adres URL określony w oryginalnym pliku HTML.  
  
## <a name="frames-and-security"></a>Ramki i zabezpieczeń  
 Dostęp do ramki jest skomplikowane faktem, że zarządzany HTML DOM implementuje środkiem bezpieczeństwa, znane jako *między ramkami skryptów zabezpieczeń*. Jeśli dokument zawiera `FRAMESET` z co najmniej dwóch `FRAME`s w różnych domenach, te `FRAME`s nie mogą współdziałać ze sobą. Innymi słowy `FRAME` , wyświetla zawartość w witrynie sieci Web nie może uzyskać dostęp do informacji w `FRAME` obsługujący takich jak witryny innych firm `http://www.adatum.com/`. To są implementowane na poziomie <xref:System.Windows.Forms.HtmlWindow> klasy. Można uzyskać ogólne informacje na temat `FRAME` hostingu z innej witryny sieci Web, takich jak adres URL, ale będzie mógł uzyskać dostępu do jego <xref:System.Windows.Forms.HtmlWindow.Document%2A> lub zmienić rozmiar lub położenie jego hostingu `FRAME` lub `IFRAME`.  
  
 Ta reguła obowiązuje także w systemie windows, które można otworzyć za pomocą <xref:System.Windows.Forms.HtmlWindow.Open%2A> i <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> metody. Jeśli okno otwierania znajduje się w innej domenie niż strona hostowana w <xref:System.Windows.Forms.WebBrowser> control, nie będzie mógł przenieść to okno, lub przejrzyj jego zawartość. Ograniczenia te są wymuszane również, jeśli używasz <xref:System.Windows.Forms.WebBrowser> formantu, aby wyświetlić witrynę sieci Web, która różni się od witryny sieci Web, używane do wdrażania aplikacji opartej na formularzach Windows. Jeśli używasz [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] używać technologii wdrażania, aby zainstalować aplikację z witryny sieci Web A, a <xref:System.Windows.Forms.WebBrowser> Aby wyświetlić witrynę sieci Web B, nie będzie dostępu do witryny sieci Web użytkownika B danych.  
  
## <a name="see-also"></a>Zobacz także

- [\<Ramka > element](https://developer.mozilla.org/docs/Web/HTML/Element/frame)
- [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](using-the-managed-html-document-object-model.md)
