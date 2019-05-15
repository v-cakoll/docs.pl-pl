---
title: Zdarzenia — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 2d263ac09cb4c9196b0d584dd5cf71182be01adc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584359"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Zdarzenie pozwala [klasy](../../../csharp/language-reference/keywords/class.md) lub obiektowi powiadomić inne klasy lub obiekty, gdy wystąpi stanie się coś istotnego. Klasa, która wysyła (lub *zgłasza*) nosi nazwę zdarzenia *wydawcy* klas, które odbierają i (lub *obsługi*) zdarzenia są wywoływane *subskrybentów* .  
  
 Typowa aplikacja C# Windows Forms lub sieci Web możesz subskrybować zdarzenia wygenerowane przez formanty, takie jak przyciski i pola listy. Można użyć Visual C# zintegrowanego środowiska programistycznego (IDE), aby przeglądać zdarzenia, które kontrolki publikuje i wybrać te, które mają być obsługiwane. Środowisko IDE zapewnia prosty sposób, aby automatycznie dodać metodę programu obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
- Określa wydawcy, gdy wydarzenie jest podniesione; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.  
  
- Zdarzenie może mieć wielu subskrybentów. Subskrybent może obsłużyć wielu zdarzeń z wielu wydawców.  
  
- Zdarzenia, które mają żadnych subskrybentów nigdy nie są wywoływane.  
  
- Zdarzenia są zazwyczaj używane w celu sygnalizowania, że akcje użytkownika, takich jak kliknięcia przycisku lub menu opcji w graficznym interfejsie użytkownika.  
  
- Gdy zdarzenie jest wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy wydarzenie jest podniesione. Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- W bibliotece klas programu .NET Framework, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy bazowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [Instrukcje: Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
- [Instrukcje:  Zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
- [Instrukcje: Użycie słownika do wystąpień zdarzeń Store](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
- [Instrukcje: Implementowanie niestandardowych metod dostępu zdarzeń](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zdarzenia](~/_csharplang/spec/classes.md#events) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaci i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczenia C# 3.0: Opanowanie podstaw C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.EventHandler>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
