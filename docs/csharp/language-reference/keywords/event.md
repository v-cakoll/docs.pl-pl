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
ms.openlocfilehash: 35a42692bc87da63c69d7ccbce1b49396a84f5a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562275"
---
# <a name="event-c-reference"></a>event (odwołanie w C#)
`event` — Słowo kluczowe jest używane do deklarowania zdarzenie w klasie wydawcy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować i wywołać zdarzenie, które używa <xref:System.EventHandler> jako podstawowego typu delegowanego. Na przykład kompletny kod, który ilustruje również musieli używać ogólnych <xref:System.EventHandler%601> delegować uprawnienia do typu i subskrybować zdarzenie i Utwórz metodę programu obsługi zdarzeń, zobacz [porady: publikowanie zdarzeń tej metody Dostosuj dotyczącymi .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Zdarzenia są specjalnym rodzajem multiemisji delegat, który można wywołać tylko z w obrębie klasy lub struktury, gdzie są deklarowane (klasa wydawcy). Jeśli inne klasy lub struktury subskrybować zdarzenie, ich metody obsługi zdarzeń będzie wywoływany, gdy klasa wydawcy wywołuje zdarzenie. Aby uzyskać więcej informacji i przykłady kodu, zobacz [zdarzenia](../../../csharp/programming-guide/events/index.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).  
  
 Zdarzenia może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md) lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Następujące modyfikatory dostępu Określ, jak użytkownicy klasy można uzyskiwać dostęp do zdarzenia. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
## <a name="keywords-and-events"></a>Słowa kluczowe i zdarzenia  
 Następujące słowa kluczowe mają zastosowanie do zdarzenia.  
  
|Słowo kluczowe|Opis|Więcej informacji|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Udostępnia zdarzenia dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli istnieje żadne wystąpienie klasy.|[Klasy statyczne i statyczne elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umożliwia klasy pochodne, aby zastąpić zachowanie zdarzeń za pomocą [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe.|[Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Określa, że dla klas pochodnych nie jest już wirtualny.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Kompilator nie wygeneruje `add` i `remove` bloków metody dostępu zdarzeń i klasy pochodne w związku z tym należy podać zapewniali własną implementację.||  
  
 Zdarzenie może być zadeklarowana jako zdarzeń statycznych przy użyciu [statyczne](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe. To udostępnienie zdarzenia dotyczące obiektów wywołujących w dowolnym momencie, nawet jeśli istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Zdarzenie może być oznaczona jako wirtualnego wydarzenia, za pomocą [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe. Dzięki temu klasy pochodne, aby zastąpić zachowanie zdarzeń za pomocą [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Zastępowanie wirtualnego wydarzenia zdarzenie może być również [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md), która określa, że dla klas pochodnych nie jest już wirtualny. Ponadto zdarzenia mogą być deklarowane [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md), co oznacza, że kompilator nie wygeneruje `add` i `remove` bloki metody dostępu zdarzeń. W związku z tym w klasach pochodnych należy podać zapewniali własną implementację.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [add](../../../csharp/language-reference/keywords/add.md)  
- [remove](../../../csharp/language-reference/keywords/remove.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
- [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
