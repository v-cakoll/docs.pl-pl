---
title: Zalety typów ogólnych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
ms.openlocfilehash: f97d3ce7a67638719d02c31879c00679405118bc
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245015"
---
# <a name="benefits-of-generics-c-programming-guide"></a>Zalety typów ogólnych (Przewodnik programowania w języku C#)
Typy ogólne zapewnia rozwiązanie do ograniczenia we wcześniejszych wersjach środowiska uruchomieniowego języka wspólnego i języki C#, w którym Generalizacja odbywa się przez rzutowanie typów do i z uniwersalnego typu bazowego <xref:System.Object>. Tworząc klasy ogólnej, można utworzyć kolekcję, która jest bezpieczna pod względem typu w czasie kompilacji.  
  
 Ograniczenia przy użyciu klasy nieogólna kolekcja wykazać, pisząc program krótki, który używa <xref:System.Collections.ArrayList> kolekcji klasy z biblioteki klas programu .NET. Wystąpienie <xref:System.Collections.ArrayList> klasy może przechowywać dowolny typ odwołanie lub wartość.  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Ale to udogodnienie są obciążone kosztami. Odwołanie lub wartość typu, który jest dodawany do <xref:System.Collections.ArrayList> jest niejawnie rzutowany w górę do <xref:System.Object>. Jeśli elementy są typami wartości, musi zostać opakowany gdy są dodawane do listy i rozpakowywany, gdy są one pobierane. Zarówno rzutowanie, jak i operacje pakowania, jak i rozpakowania obniżyć wydajność; efekt pakowania i rozpakowywania może być bardzo istotne znaczenie w scenariuszach, gdzie należy iteracja dużych kolekcjach.  
  
 Inne ograniczenia to Brak typu w czasie kompilacji sprawdzania; Ponieważ <xref:System.Collections.ArrayList> rzutuje do <xref:System.Object>, nie ma żadnego sposobu, w czasie kompilacji, aby uniemożliwić wykonywanie coś takich przez kod klienta:  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Mimo że doskonale dopuszczalne i czasami zamierzone, w przypadku tworzenia kolekcji heterogenicznych, łączenie ciągów i `ints` w jednym <xref:System.Collections.ArrayList> najprawdopodobniej jest to błąd programistyczny, a ten błąd nie zostanie wykryty aż do czasu.  
  
 W wersjach 1.0 i 1.1 programu w języku C# można uniknąć zagrożeń ogólnych kodu w klas kolekcji .NET Framework klasy podstawowej biblioteki pisząc własne kolekcje określonego typu. Oczywiście ponieważ taka klasa nie jest wielokrotnego użytku dla więcej niż jednego typu danych, tracisz korzyści generalizacji i trzeba ponownie pisać klasy dla każdego typu, które będą przechowywane.  
  
 Co <xref:System.Collections.ArrayList> i innych podobnych klas naprawdę potrzebne jest sposób w przypadku kodu klienta określić, na podstawie poszczególnych wystąpień danego typu danych określonego będą one używane. Który może wyeliminować konieczność stosowania rozszerzające do <xref:System.Object> i będzie również umożliwiać przez kompilator kontrola typów. Innymi słowy <xref:System.Collections.ArrayList> wymaga parametru typu. Dokładnie to zapewniają ogólne. W ogólnej <xref:System.Collections.Generic.List%601> kolekcji w <xref:System.Collections.Generic> przestrzeni nazw, w tej samej operacji dodawania elementów do kolekcji jest podobny do tego:  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 W przypadku kodu klienta, tylko dodać składni <xref:System.Collections.Generic.List%601> w porównaniu do <xref:System.Collections.ArrayList> jest argumentem typu w deklaracji i konkretyzacji. Poinformowanie tę złożoność nieco bardziej kodowania, można utworzyć listę, która jest nie tylko bezpieczniejszy niż <xref:System.Collections.ArrayList>, ale również znacznie szybsze, szczególnie w przypadku, gdy elementy listy są typami wartości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Konwersja boxing i konwersja unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)  
- [Wytyczne dotyczące kolekcji](../../../standard/design-guidelines/guidelines-for-collections.md)   
