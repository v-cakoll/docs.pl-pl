---
title: Zdarzenia — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712315"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Zdarzenia umożliwiają [klasy](../../language-reference/keywords/class.md) lub obiektu, aby powiadomić inne klasy lub obiekty, gdy coś interesującego występuje. Klasa, która wysyła (lub *wywołuje)* zdarzenie jest wywoływana *wydawcy* i klas, które odbierają (lub *doobsługi)* zdarzenie są nazywane *subskrybentów*.  
  
W typowej aplikacji C# Windows Forms lub Web użytkownik subskrybuje zdarzenia wywoływane przez formanty, takie jak przyciski i pola listy. Można użyć visual c# zintegrowane środowisko programistyczne (IDE) do przeglądania zdarzeń, które formant publikuje i wybrać te, które mają obsługiwać. IDE zapewnia łatwy sposób automatycznego dodawania metody obsługi pustych zdarzeń i kodu do subskrybowania zdarzenia. Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](./how-to-subscribe-to-and-unsubscribe-from-events.md)
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
- Wydawca określa, kiedy zdarzenie jest wywoływane; subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.  
  
- Zdarzenie może mieć wielu subskrybentów. Subskrybent może obsługiwać wiele zdarzeń od wielu wydawców.  
  
- Zdarzenia, które nie mają subskrybentów nigdy nie są wywoływane.  
  
- Zdarzenia są zwykle używane do sygnalizowania działań użytkownika, takich jak kliknięcia przycisków lub wybór menu w graficznych interfejsach użytkownika.  
  
- Gdy zdarzenie ma wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest wywoływane. Aby wywołać zdarzenia asynchronicznie, zobacz [Wywoływanie metod synchronicznych asynchronicznie](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- W bibliotece klas .NET Framework zdarzenia <xref:System.EventHandler> są oparte <xref:System.EventArgs> na delegowaniu i klasie podstawowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](./how-to-raise-base-class-events-in-derived-classes.md)

- [Implementowanie zdarzeń interfejsu](./how-to-implement-interface-events.md)

- [Implementowanie niestandardowych metod dostępu zdarzeń](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Zdarzenia](~/_csharplang/spec/classes.md#events) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegaci, zdarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów Języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaci i wydarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [nauce C# 3.0: Opanuj podstawy języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.EventHandler>
- [Przewodnik programowania języka C#](../index.md)
- [Delegaty](../delegates/index.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
