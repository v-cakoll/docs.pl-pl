---
title: interfejs — odwołanie do języka C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625855"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(Odwołanie do języka C#)

Interfejs definiuje kontrakt. Wszelkie [`class`](class.md) [`struct`](../builtin-types/struct.md) lub implementuje tej umowy musi zapewnić implementację elementów członkowskich zdefiniowanych w interfejsie. Począwszy od języka C# 8.0, interfejs może zdefiniować implementację domyślną dla elementów członkowskich. Może również [`static`](static.md) zdefiniować elementy członkowskie w celu zapewnienia jednej implementacji dla wspólnych funkcji.

W poniższym przykładzie `ImplementationClass` klasa musi `SampleMethod` implementować metodę o `void`nazwie, która nie ma parametrów i zwraca .

Aby uzyskać więcej informacji i przykładów, zobacz [Interfejsy](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Interfejs może być członkiem obszaru nazw lub klasy. Deklaracja interfejsu może zawierać deklaracje (podpisy bez implementacji) następujących elementów członkowskich:

- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexers](../../programming-guide/indexers/using-indexers.md) (Indeksatory)
- [Zdarzenia](event.md)

Te poprzednie deklaracje elementów członkowskich zazwyczaj nie zawierają treści. Począwszy od języka C# 8.0, element członkowski interfejsu może zadeklarować treść. Jest to nazywane *domyślną implementacją*. Elementy członkowskie z organami pozwalają interfejsowi, aby zapewnić "domyślną" implementację dla klas i struktur, które nie zapewniają implementacji nadrzędnej. Ponadto począwszy od języka C# 8.0 interfejs może zawierać:

- [Stałe](const.md)
- [Operatory](../operators/operator-overloading.md)
- [Konstruktor statyczny](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md)
- [Pola statyczne, metody, właściwości, indeksatory i zdarzenia](static.md)
- Deklaracje członkowskie przy użyciu składni implementacji interfejsu jawnego.
- Modyfikatory dostępu jawnego [`public`](access-modifiers.md)(domyślnym dostępem jest ).

Interfejsy mogą nie zawierać stanu wystąpienia. Podczas gdy pola statyczne są teraz dozwolone, pola wystąpień nie są dozwolone w interfejsach. [Wystąpienia właściwości automatyczne](../../programming-guide/classes-and-structs/auto-implemented-properties.md) nie są obsługiwane w interfejsach, ponieważ będą one niejawnie zadeklarować ukryte pole. Ta reguła ma subtelny wpływ na deklaracje właściwości. W deklaracji interfejsu następujący kod nie deklaruje właściwości zaimplementowanej automatycznie, `class` `struct`tak jak w a lub . Zamiast tego deklaruje właściwość, która nie ma implementacji domyślnej, ale musi być zaimplementowana w dowolnym typie, który implementuje interfejs:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Interfejs można dziedziczyć z jednego lub więcej interfejsów podstawowych. Gdy interfejs [zastępuje metodę](override.md) zaimplementowane w interfejsie podstawowym, należy użyć składni [implementacji interfejsu jawnego.](../../programming-guide/interfaces/explicit-interface-implementation.md)

Gdy lista typów podstawowych zawiera klasę podstawową i interfejsy, klasa podstawowa musi być na pierwszym miejscu na liście.

Klasa, która implementuje interfejs może jawnie implementować elementy członkowskie tego interfejsu. Jawnie zaimplementowany element członkowski nie może być dostępny za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu. Ponadto domyślne elementy członkowskie interfejsu są dostępne tylko za pośrednictwem wystąpienia interfejsu.

Aby uzyskać więcej informacji na temat implementacji interfejsu jawnego, zobacz [Implementacja interfejsu jawnego](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono implementację interfejsu. W tym przykładzie interfejs zawiera deklarację właściwości i klasa zawiera implementację. Każde wystąpienie klasy, która `IPoint` implementuje ma `x` właściwości `y`całkowite i .

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [interfaces](~/_csharplang/spec/interfaces.md) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i specyfikacji funkcji dla [domyślnych elementów członkowskich interfejsu — C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
- [Używanie właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Używanie indeksatorów](../../programming-guide/indexers/using-indexers.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
