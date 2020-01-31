---
title: Klasy bazowe na potrzeby implementowania abstrakcji
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
ms.openlocfilehash: b22923338f8488b6f7684e565f62d9afc16e6aa0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741779"
---
# <a name="base-classes-for-implementing-abstractions"></a>Klasy bazowe na potrzeby implementowania abstrakcji
Ściśle mówiąc, Klasa jest klasą bazową, gdy tworzona jest inna Klasa. Jednak na potrzeby tej sekcji Klasa bazowa jest klasą zaprojektowaną głównie w celu zapewnienia wspólnego abstrakcji lub innych klas do wielokrotnego użycia implementacji domyślnej, chociaż dziedziczenia. Klasy bazowe zwykle znajdują się w środku hierarchii dziedziczenia, między abstrakcją w katalogu głównym hierarchii a kilkoma implementacjami niestandardowymi w dolnej części.

 Służą one jako pomocnicy implementacji do implementowania abstrakcji. Na przykład jedna z streszczeń struktury dla uporządkowanych kolekcji elementów jest interfejsem <xref:System.Collections.Generic.IList%601>. Implementowanie <xref:System.Collections.Generic.IList%601> nie jest proste i dlatego struktura zawiera kilka klas bazowych, takich jak <xref:System.Collections.ObjectModel.Collection%601> i <xref:System.Collections.ObjectModel.KeyedCollection%602>, które pomagają jako pomocnicy do implementowania kolekcji niestandardowych.

 Klasy bazowe zazwyczaj nie są odpowiednie do obsłużenia jako abstrakcje, ponieważ mogą zawierać zbyt wiele implementacji. Na przykład klasa bazowa `Collection<T>` zawiera wiele implementacji związanych z tym faktem, że implementuje interfejs nieogólny `IList` (w celu usprawnienia integracji z kolekcjami nieogólnymi) i jest to kolekcja elementów przechowywanych w pamięci w jednym z jej pól.

 Jak wspomniano wcześniej, klasy bazowe mogą zapewniać niecenną pomoc dla użytkowników, którzy muszą wdrożyć streszczenia, ale jednocześnie mogą być znaczną odpowiedzialnością. Dodają obszar powierzchni i zwiększają głębokość hierarchii dziedziczenia, a więc koncepcje komplikują strukturę. W związku z tym klasy bazowe powinny być używane tylko wtedy, gdy zapewniają użytkownikom struktury znaczącą wartość. Należy je unikać, jeśli zapewniają wartość tylko dla realizatorów struktury, w takim przypadku delegowanie do wewnętrznej implementacji zamiast dziedziczenia z klasy bazowej powinno być silnie rozważane.

 ✔️ ROZWAŻYĆ tworzenie klas podstawowych, nawet jeśli nie zawierają żadnych abstrakcyjnych elementów członkowskich. To wyraźnie komunikuje się z użytkownikami, do których Klasa została zaprojektowana wyłącznie do dziedziczenia.

 ✔️ Rozważ umieszczenie klas bazowych w oddzielnym obszarze nazw z typów scenariuszy linii głównej. Według definicji klasy bazowe są przeznaczone dla zaawansowanych scenariuszy rozszerzalności, dlatego nie są one interesujące dla większości użytkowników.

 ❌ uniknąć nadawania nazw klasom bazowym sufiksem "Base", jeśli klasa jest przeznaczona do użycia w publicznych interfejsach API.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
