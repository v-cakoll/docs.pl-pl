---
title: Zdarzenia (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 4031ff08bee945f019974ad590e9b3df6d9c263c
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086235"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Zdarzenie pozwala [klasy](../../../csharp/language-reference/keywords/class.md) lub obiektowi powiadomić inne klasy lub obiekty, gdy wystąpi stanie się coś istotnego. Klasa, która wysyła (lub *zgłasza*) nosi nazwę zdarzenia *wydawcy* klas, które odbierają i (lub *obsługi*) zdarzenia są wywoływane *subskrybentów* .  
  
 Typowa aplikacja C# Windows Forms lub sieci Web możesz subskrybować zdarzenia wygenerowane przez formanty, takie jak przyciski i pola listy. Można użyć Visual C# zintegrowanego środowiska programistycznego (IDE), aby przeglądać zdarzenia, które kontrolki publikuje i wybrać te, które mają być obsługiwane. IDE automatycznie dodaje metodę programu obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
-   Określa wydawcy, gdy wydarzenie jest podniesione; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.  
  
-   Zdarzenie może mieć wielu subskrybentów. Subskrybent może obsłużyć wielu zdarzeń z wielu wydawców.  
  
-   Zdarzenia, które mają żadnych subskrybentów nigdy nie są wywoływane.  
  
-   Zdarzenia są zazwyczaj używane w celu sygnalizowania, że akcje użytkownika, takich jak kliknięcia przycisku lub menu opcji w graficznym interfejsie użytkownika.  
  
-   Gdy zdarzenie jest wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy wydarzenie jest podniesione. Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   W [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy bazowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Instrukcje: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Instrukcje: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi platformy .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Instrukcje: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Porady: zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Instrukcje: użycie słownika do przechowywania wystąpień zdarzeń](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Instrukcje: implementowanie niestandardowych metod dostępu zdarzeń](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegatów, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, wydanie trzecie: ponad 250 rozwiązań dla programistów C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegaci i zdarzenia](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) w [Nauka języka C# 3.0: Opanuj podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.EventHandler>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)  
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
