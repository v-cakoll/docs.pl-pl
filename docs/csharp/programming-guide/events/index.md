---
title: "Zdarzenia (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f714bded446e62ac6165d691d2404249275178e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Włącz zdarzenia [klasy](../../../csharp/language-reference/keywords/class.md) lub obiekt, aby powiadomić innych klas lub obiekty coś odsetek sytuacji. Klasa, która wysyła (lub *zgłasza*) zdarzenie jest wywoływane *wydawcy* klasy, które odbierają i (lub *obsługi*) zdarzenia są nazywane *subskrybentów* .  
  
 Typowa aplikacja formularzy systemu Windows w języku C# lub sieci Web należy subskrybować zdarzenia generowane przez formanty, takie jak przycisków i pola listy. Można użyć [!INCLUDE[csprcs](~/includes/csprcs-md.md)] zintegrowane środowisko programistyczne (IDE), aby przeglądać zdarzenia, które publikuje formantu i wybrać te, które mają być obsługiwane. IDE automatycznie dodaje metoda obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
-   Określa wydawcy, gdy zdarzenie jest wywoływane; subskrybentów określają, jakie działanie jest wykonywane w odpowiedzi na zdarzenia.  
  
-   Zdarzenie może mieć wielu subskrybentów. Subskrybent może obsługiwać wiele zdarzeń z wielu wydawcy.  
  
-   Zdarzenia, które mają subskrybentów. nigdy nie są zgłaszane.  
  
-   Zdarzenia są zwykle używane w celu zasygnalizowania akcje użytkownika, takie jak kliknięcia przycisków lub menu opcji w graficznym interfejsie użytkownika.  
  
-   Zdarzenia po wielu subskrybentów obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest wywoływane. Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](https://msdn.microsoft.com/library/2e08f6yc).  
  
-   W [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy podstawowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Porady: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Porady: zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Synchronizacja wątku](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Porady: użycie słownika do przechowywania wystąpień zdarzeń](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Porady: Implementowanie niestandardowych metod dostępu zdarzeń](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Obiekty delegowane, zdarzeń i wyrażenia Lambda](http://go.microsoft.com/fwlink/?LinkId=195395) w [C# 3.0 Cookbook, trzecia edycja: ponad 250 rozwiązań dla programistów języka C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegaci i zdarzenia](http://go.microsoft.com/fwlink/?LinkId=195418) w [Learning C# 3.0: wzorca podstawy języka C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.EventHandler>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](https://msdn.microsoft.com/library/dacysss4.aspx)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](https://msdn.microsoft.com/library/hkasytyf)
