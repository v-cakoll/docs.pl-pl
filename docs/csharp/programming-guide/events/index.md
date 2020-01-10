---
title: Zdarzenia — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712315"
---
# <a name="events-c-programming-guide"></a>Zdarzenia (Przewodnik programowania w języku C#)
Zdarzenia umożliwiają [klasie](../../language-reference/keywords/class.md) lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania. Klasa, która wysyła (lub *podnosi*) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub *obsługują*) zdarzenie są nazywane *subskrybentami*.  
  
W typowej C# Windows Forms lub aplikacji sieci Web subskrybujesz zdarzenia wywoływane przez kontrolki, takie jak przyciski i pola listy. Przy użyciu C# zintegrowanego środowiska programistycznego (IDE) można przeglądać zdarzenia publikowane przez formant i wybierać te, które mają być obsługiwane. Środowisko IDE zapewnia łatwy sposób automatycznego dodawania pustej metody obsługi zdarzeń i kodu w celu subskrybowania zdarzenia. Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md).
  
## <a name="events-overview"></a>Przegląd zdarzeń  
 Zdarzenia mają następujące właściwości:  
  
- Wydawca określa, kiedy zdarzenie jest zgłaszane; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.  
  
- Wydarzenie może mieć wielu subskrybentów. Subskrybenci mogą obsługiwać wiele zdarzeń z wielu wydawców.  
  
- Zdarzenia, które nie mają subskrybentów nigdy nie są zgłaszane.  
  
- Zdarzenia są zwykle używane do sygnalizowania akcji użytkownika, takich jak kliknięcia przycisków lub menu w graficznym interfejsie użytkownika.  
  
- Gdy zdarzenie ma wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest zgłaszane. Aby wywoływać zdarzenia asynchronicznie, zobacz [wywoływanie metod synchronicznych asynchronicznie](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- W bibliotece klas .NET Framework zdarzenia są oparte na delegatze <xref:System.EventHandler> i <xref:System.EventArgs> klasie bazowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych](./how-to-raise-base-class-events-in-derived-classes.md)

- [Jak zaimplementować zdarzenia interfejsu](./how-to-implement-interface-events.md)

- [Jak zaimplementować niestandardowe metody dostępu do zdarzeń](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zdarzenia](~/_csharplang/spec/classes.md#events) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="featured-book-chapters"></a>Polecane rozdziały książki  
 [Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: więcej niż 250 rozwiązań dla C# 3,0 programistów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegaty i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczeniu C# 3,0: główne podstawy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.EventHandler>
- [Przewodnik programowania w języku C#](../index.md)
- [Delegaci](../delegates/index.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
