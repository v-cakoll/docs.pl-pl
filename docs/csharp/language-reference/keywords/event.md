---
title: event (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: b58e06c87ebf601daf231c83993ebe512f51ecd9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955969"
---
# <a name="event-c-reference"></a>event (odwołanie w C#)
`event` — Słowo kluczowe służy do deklarowania zdarzenia w klasie wydawcy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób deklarowanie i wywoływanie zdarzeń, który używa <xref:System.EventHandler> jako podstawowego typu delegowanego. Na przykład kompletny kod, który również pokazano, jak używać ogólnych <xref:System.EventHandler%601> delegować typu i subskrybowanie zdarzeń i utworzyć metoda obsługi zdarzeń, zobacz [porady: publikowanie zdarzeń tej metody Dostosuj wskazówkami dotyczącymi .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Zdarzenia są specjalny rodzaj multiemisji delegata, który można wywołać tylko z wewnątrz klasy lub struktury, w którym je zadeklarowano (klasa wydawcy). Jeśli inne klasy lub struktury subskrybować zdarzenia, ich metody obsługi zdarzeń będzie wywoływany, gdy klasa wydawcy wywołuje zdarzenie. Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [zdarzenia](../../../csharp/programming-guide/events/index.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).  
  
 Zdarzenia może być oznaczony jako [publicznego](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). Te modyfikatory dostępu zdefiniuj, jak użytkownicy klasy mają dostęp do zdarzenia. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Słowa kluczowe i zdarzenia  
 Poniższe słowa kluczowe zastosować do zdarzenia.  
  
|Słowo kluczowe|Opis|Więcej informacji|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Udostępnia zdarzenia dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli nie ma wystąpień klasy.|[Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umożliwia klasy pochodne zastąpić zachowanie zdarzeń za pomocą [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe.|[Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Określa, że dla klas pochodnych nie jest już wirtualnego.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Kompilator nie będą generowane `add` i `remove` bloków metody dostępu zdarzeń i w związku z tym pochodne podać własne implementacji.||  
  
 Zdarzenia mogą być deklarowane jako statyczne zdarzenie przy użyciu [statycznych](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe. To udostępnienie zdarzenia dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli nie ma wystąpień klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Zdarzenie może być oznaczony jako wirtualny zdarzeń za pomocą [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe. Dzięki temu klasy pochodne zastąpić zachowanie zdarzeń za pomocą [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Zdarzenie zastępowanie wirtualnego zdarzeń można też [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), który określa, że dla klas pochodnych nie jest już wirtualny. Na koniec zdarzenia mogą być deklarowane [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md), co oznacza, że nie będą generowane przez kompilator `add` i `remove` bloki metody dostępu zdarzenia. W związku z tym Klasa pochodna musi zapewniać ich implementacji.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [add](../../../csharp/language-reference/keywords/add.md)  
 [remove](../../../csharp/language-reference/keywords/remove.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
