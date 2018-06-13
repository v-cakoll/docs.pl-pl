---
title: Zdarzenia (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 5b844b20ac62b4cbc2a73931eecab95f22b4b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339920"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Włącz zdarzenia [klasy](../../../csharp/language-reference/keywords/class.md) lub obiekt, aby powiadomić innych klas lub obiekty coś odsetek sytuacji. Klasa, która wysyła (lub *zgłasza*) zdarzenie jest wywoływane *wydawcy* klasy, które odbierają i (lub *obsługi*) zdarzenia są nazywane *subskrybentów* .  
  
 Typowa aplikacja formularzy systemu Windows w języku C# lub sieci Web należy subskrybować zdarzenia generowane przez formanty, takie jak przycisków i pola listy. Visual C# zintegrowane środowisko programistyczne (IDE) umożliwia przeglądanie zdarzeń, które publikuje formantu i wybrać te, które mają być obsługiwane. IDE automatycznie dodaje metoda obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
-   Określa wydawcy, gdy zdarzenie jest wywoływane; subskrybentów określają, jakie działanie jest wykonywane w odpowiedzi na zdarzenia.  
  
-   Zdarzenie może mieć wielu subskrybentów. Subskrybent może obsługiwać wiele zdarzeń z wielu wydawcy.  
  
-   Zdarzenia, które mają subskrybentów. nigdy nie są zgłaszane.  
  
-   Zdarzenia są zwykle używane w celu zasygnalizowania akcje użytkownika, takie jak kliknięcia przycisków lub menu opcji w graficznym interfejsie użytkownika.  
  
-   Zdarzenia po wielu subskrybentów obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest wywoływane. Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   W [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy podstawowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Instrukcje: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Instrukcje: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi platformy .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Instrukcje: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Porady: zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Synchronizacja wątku](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Instrukcje: użycie słownika do przechowywania wystąpień zdarzeń](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Instrukcje: implementowanie niestandardowych metod dostępu zdarzeń](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Obiekty delegowane, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, trzecia edycja: ponad 250 rozwiązań dla programistów języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegaci i zdarzenia](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) w [Learning C# 3.0: wzorca podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.EventHandler>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
