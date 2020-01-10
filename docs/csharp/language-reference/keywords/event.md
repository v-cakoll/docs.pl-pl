---
title: C# informacje o zdarzeniu
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713554"
---
# <a name="event-c-reference"></a>zdarzenie (C# odwołanie)

Słowo kluczowe `event` jest używane do deklarowania zdarzenia w klasie wydawcy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować i zgłosić zdarzenie, które używa <xref:System.EventHandler> jako bazowego typu delegata. Aby zapoznać się z kompletnym przykładem kodu, który pokazuje, jak używać ogólnego typu delegata <xref:System.EventHandler%601> i jak subskrybować zdarzenie i utworzyć metodę obsługi zdarzeń, zobacz [How to Publish Events, które są zgodne z wytycznymi .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Zdarzenia są specjalnym rodzajem delegatów multiemisji, który można wywołać tylko z poziomu klasy lub struktury, w której są zadeklarowane (Klasa wydawcy). Jeśli inne klasy lub struktury subskrybują zdarzenie, ich metody obsługi zdarzeń będą wywoływane, gdy Klasa wydawcy zgłasza zdarzenie. Aby uzyskać więcej informacji i przykładów kodu, zobacz [Events](../../programming-guide/events/index.md) and [delegats](../../programming-guide/delegates/index.md).

Zdarzenia mogą być oznaczone jako [publiczne](./public.md), [prywatne](./private.md), [chronione](./protected.md), [wewnętrzne](./internal.md), [chronione wewnętrznie](./protected-internal.md)lub [chronione prywatnie](./private-protected.md). Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą uzyskać dostęp do zdarzenia. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Słowa kluczowe i zdarzenia

Poniższe słowa kluczowe mają zastosowanie do zdarzeń.

|Słowo kluczowe|Opis|Więcej informacji|
|-------------|-----------------|--------------------------|
|[static](./static.md)|Sprawia, że zdarzenie jest dostępne dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy.|[Klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Umożliwia klasom pochodnym przesłonięcie zachowania zdarzenia za pomocą słowa kluczowego [override](./override.md) .|[Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Określa, że dla klas pochodnych nie jest już wirtualna.||
|[abstract](./abstract.md)|Kompilator nie będzie generował `add` i `remove` bloków dostępu zdarzeń, dlatego klasy pochodne muszą zapewnić własną implementację.||

Zdarzenie może być zadeklarowane jako zdarzenie statyczne za pomocą słowa kluczowego [static](./static.md) . To sprawia, że zdarzenie jest dostępne dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Zdarzenie może być oznaczone jako zdarzenie wirtualne przy użyciu słowa kluczowego [Virtual](./virtual.md) . Dzięki temu klasy pochodne zastępują zachowanie zdarzeń za pomocą słowa kluczowego [override](./override.md) . Aby uzyskać więcej informacji, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md). Zdarzenie przesłaniające zdarzenie wirtualne może być również [zapieczętowane](./sealed.md), które określa, że dla klas pochodnych nie jest już wirtualna. Na koniec zdarzenie może być zadeklarowane jako [abstract](./abstract.md), co oznacza, że kompilator nie generuje bloków dostępu do zdarzeń `add` i `remove`. W związku z tym klasy pochodne muszą dostarczać własne implementacje.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [Modyfikatory](index.md)
- [Jak łączyć delegatów (delegatów multiemisji)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
