---
title: modyfikator statyczny — odwołanie do języka C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76744660"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)

`static` Modyfikator służy do deklarowania statyczny element członkowski, który należy do samego typu, a nie do określonego obiektu. Modyfikator `static` może służyć `static` do deklarowania klas. W klasach, interfejsów i struktur, można `static` dodać modyfikator do pól, metody, właściwości, operatory, zdarzenia i konstruktorów. Modyfikator `static` nie może być używany z indeksatorów lub finalizatorów. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Przykład

Następująca klasa jest `static` zadeklarowana `static` jako i zawiera tylko metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklaracja stała lub typ `static` jest niejawnie element członkowski. Nie `static` można odwoływać się do elementu członkowskiego za pośrednictwem wystąpienia. Zamiast tego odwołuje się do niego za pomocą nazwy typu. Rozważmy na przykład następującą klasę:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Aby odwołać `static` `x`się do członka, należy `MyBaseC.MyStruct.x`użyć w pełni kwalifikowanej nazwy, chyba że element członkowski jest dostępny z tego samego zakresu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Wystąpienie klasy zawiera oddzielną kopię wszystkich pól instancji klasy, istnieje tylko jedna `static` kopia każdego pola.

Nie jest możliwe użycie [`this`](this.md) do `static` metod odwołania lub akcesorów właściwości.

Jeśli `static` słowo kluczowe jest stosowane do klasy, wszyscy członkowie `static`klasy muszą być .

Klasy, interfejsy `static` i klasy `static` mogą mieć konstruktorów. Konstruktor `static` jest wywoływana w pewnym momencie między rozpoczęciem programu i klasy jest tworzone.

> [!NOTE]
> Słowo `static` kluczowe ma bardziej ograniczone zastosowania niż w języku C++. Aby porównać ze słowem kluczowym C++, zobacz [Klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).

Aby `static` zademonstrować członków, należy wziąć pod uwagę klasę, która reprezentuje pracownika firmy. Załóżmy, że klasa zawiera metodę do zliczania pracowników i pole do przechowywania liczby pracowników. Zarówno metoda, jak i pole nie należą do żadnego wystąpienia pracownika. Zamiast tego należą do całej klasy pracowników. Powinny one być `static` zadeklarowane jako członkowie klasy.

## <a name="example"></a>Przykład

W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika o jeden i wyświetla informacje dla nowego pracownika i nowej liczby pracowników. Ten program odczytuje bieżącą liczbę pracowników z klawiatury.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Przykład

W tym przykładzie pokazano, `static` że można `static` zainicjować pole przy użyciu innego pola, które nie zostało jeszcze zadeklarowane. Wyniki będą niezdefiniowane, dopóki nie zostanie jawnie `static` przypisana wartość do pola.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Klasy statyczne i statyczni członkowie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
