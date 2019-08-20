---
title: Zdarzenia — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 7a8a8e6b6a393f151d69d1879f475e04f44df5fa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590384"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Zdarzenia umożliwiają [klasie](../../language-reference/keywords/class.md) lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania. Klasa, która wysyła (lub *podnosi*) zdarzenie, jest nazywana wydawcą i klasy, które odbierają (lub *obsługują*) zdarzenie są nazywane *subskrybentami*.  
  
 W typowej C# Windows Forms lub aplikacji sieci Web subskrybujesz zdarzenia wywoływane przez kontrolki, takie jak przyciski i pola listy. Przy użyciu C# zintegrowanego środowiska programistycznego (IDE) można przeglądać zdarzenia publikowane przez formant i wybierać te, które mają być obsługiwane. Środowisko IDE zapewnia łatwy sposób automatycznego dodawania pustej metody obsługi zdarzeń i kodu w celu subskrybowania zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
- Wydawca określa, kiedy zdarzenie jest zgłaszane; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.  
  
- Wydarzenie może mieć wielu subskrybentów. Subskrybenci mogą obsługiwać wiele zdarzeń z wielu wydawców.  
  
- Zdarzenia, które nie mają subskrybentów nigdy nie są zgłaszane.  
  
- Zdarzenia są zwykle używane do sygnalizowania akcji użytkownika, takich jak kliknięcia przycisków lub menu w graficznym interfejsie użytkownika.  
  
- Gdy zdarzenie ma wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest zgłaszane. Aby wywoływać zdarzenia asynchronicznie, zobacz [wywoływanie metod synchronicznych asynchronicznie](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- W bibliotece klas .NET Framework zdarzenia są oparte na <xref:System.EventHandler> delegatze <xref:System.EventArgs> i klasie bazowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Instrukcje: Subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [Instrukcje: Publikuj zdarzenia zgodne z wytycznymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [Instrukcje: Wywołaj zdarzenia klasy podstawowej w klasach pochodnych](./how-to-raise-base-class-events-in-derived-classes.md)  
  
- [Instrukcje:  Implementowanie zdarzeń interfejsu](./how-to-implement-interface-events.md)  
  
- [Instrukcje: Implementowanie niestandardowych metod dostępu do zdarzeń](./how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zdarzenia](~/_csharplang/spec/classes.md#events) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: Ponad 250 rozwiązań dla C# programistów 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaci i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczeniu C# 3,0: Główne podstawy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.EventHandler>
- [Przewodnik programowania w języku C#](../index.md)
- [Delegaty](../delegates/index.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
