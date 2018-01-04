---
title: "Uzyskiwanie dostępu do ramek w modelu DOM (Document Object Model) zarządzanych dokumentów HTML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9355596982025bf9834924a0de8e79e7073fc0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Uzyskiwanie dostępu do ramek w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Niektóre dokumenty HTML składają się z *ramki*, lub okna, które mogą przechowywać swoich własnych różne dokumentów HTML. Za pomocą ramek można łatwo tworzyć strony HTML, w których statycznych, takich jak pasek nawigacyjny pozostały jedną lub kilka części strony, podczas gdy inne ramki stale zmienić jego zawartość.  
  
 HTML autorzy mogą tworzyć ramki w jeden z dwóch sposobów:  
  
-   Przy użyciu `FRAMESET` i `FRAME` tagów, co spowoduje utworzenie stałego systemu windows.  
  
 —lub—  
  
-   Przy użyciu `IFRAME` tagu, który tworzy okno przestawne, które można zmienić ich pozycji w czasie wykonywania.  
  
1.  Ponieważ ramki zawierają dokumentów HTML, są one reprezentowane w modelu DOM (Document Object) jako elementy okna i elementy ramki.  
  
2.  Podczas uzyskiwania dostępu `FRAME` lub `IFRAME` tagu za pomocą kolekcji ramki <xref:System.Windows.Forms.HtmlWindow>, są pobierane elementu okna odpowiadającego ramki. Ta pozycja reprezentuje wszystkie ramki właściwości dynamicznych, takich jak bieżący adres URL, dokumentów i rozmiar.  
  
3.  Podczas uzyskiwania dostępu `FRAME` lub `IFRAME` tagu za pomocą <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> właściwość <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> kolekcji lub metod, takich jak <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> lub <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, są pobierane elementu ramki. Reprezentuje statycznej właściwości ramki, w tym adres URL określony w oryginalnym pliku w formacie HTML.  
  
## <a name="frames-and-security"></a>Ramki i zabezpieczenia  
 Dostęp do ramki jest złożona faktem, że zarządzany HTML DOM implementuje miary zabezpieczeń znany jako *między ramkami skryptów zabezpieczeń*. Jeśli dokument zawiera `FRAMESET` z co najmniej dwa `FRAME`s w różnych domenach, te `FRAME`s nie mogą oddziaływać na siebie. Innymi słowy `FRAME` czy wyświetla zawartość z witryny sieci Web nie może uzyskać dostępu informacji w `FRAME` obsługującego witryn innych firm, takich jak http://www.adatum.com/. Zaimplementowano zabezpieczeń na poziomie <xref:System.Windows.Forms.HtmlWindow> klasy. Możesz uzyskać informacje ogólne o `FRAME` hosting innej witryny sieci Web, takie jak adres URL, ale nie będzie można uzyskać dostępu do jego <xref:System.Windows.Forms.HtmlWindow.Document%2A> lub zmień rozmiar lub lokalizację jego hosting `FRAME` lub `IFRAME`.  
  
 Ta zasada ma zastosowanie również do systemu windows, które można otworzyć za pomocą <xref:System.Windows.Forms.HtmlWindow.Open%2A> i <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> metody. Jeśli okno otwierania jest w innej domenie na stronie hostowanych w <xref:System.Windows.Forms.WebBrowser> kontroli, nie można przenosić tego okna i przejrzyj jego zawartość. Te ograniczenia również są wymuszane, jeśli używasz <xref:System.Windows.Forms.WebBrowser> formantu, aby wyświetlić witrynę sieci Web, która różni się od witryny sieci Web umożliwia wdrażanie aplikacji opartych na formularzach systemu Windows. Jeśli używasz [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] technologii wdrażania, aby zainstalować aplikację z witryny sieci Web A i użyj <xref:System.Windows.Forms.WebBrowser> do wyświetlenia B witryny sieci Web, nie będzie możliwe do witryny sieci Web access B danych.  
  
 Aby uzyskać więcej informacji na temat skryptów między witrynami temacie[o wykonywania skryptów i zabezpieczeń](http://msdn.microsoft.com/library/ms533028.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Element ramki &#124; ramki obiektu](http://msdn.microsoft.com/library/ms535250.aspx)  
 [Używanie modelu DOM (Document Object Model) zarządzanych dokumentów HTML](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
