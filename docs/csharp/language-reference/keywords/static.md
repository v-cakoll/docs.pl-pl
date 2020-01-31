---
title: modyfikator statyczny C# -odwołanie
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744660"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)

Użyj modyfikatora `static`, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu. Modyfikator `static` może służyć do deklarowania klas `static`. W klasach, interfejsach i strukturach można dodać modyfikator `static` do pól, metod, właściwości, operatorów, zdarzeń i konstruktorów. Modyfikator `static` nie może być używany z indeksatorami lub finalizatorami. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Przykład

Następująca Klasa jest zadeklarowana jako `static` i zawiera tylko metody `static`:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklaracja stałej lub typu jest niejawnie elementem członkowskim `static`. Nie można odwołać się do elementu członkowskiego `static` za pomocą wystąpienia. Zamiast tego jest przywoływany przez nazwę typu. Rozważmy na przykład następujące klasy:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Aby odwołać się do `x`składowej `static`, użyj w pełni kwalifikowanej nazwy `MyBaseC.MyStruct.x`, chyba że element członkowski jest dostępny z tego samego zakresu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Chociaż wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia klasy, istnieje tylko jedna kopia każdego pola `static`.

Nie jest możliwe używanie [`this`](this.md) do odwoływania się do `static` metod lub metody dostępu do właściwości.

Jeśli `static` słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy muszą być `static`.

Klasy, interfejsy i klasy `static` mogą mieć `static` konstruktorów. Konstruktor `static` jest wywoływany w pewnym momencie od momentu uruchomienia programu i wystąpienia klasy.

> [!NOTE]
> Słowo kluczowe `static` ma więcej ograniczonych użycia niż C++w. Aby porównać ze C++ słowem kluczowym, zobacz [klasyC++magazynu ()](/cpp/cpp/storage-classes-cpp#static).

Aby wykazać składowe `static`, należy rozważyć klasę, która reprezentuje pracownika firmy. Załóżmy, że Klasa zawiera metodę służącą do policzania pracowników i pola do przechowywania liczby pracowników. Zarówno Metoda, jak i pole nie należy do żadnego wystąpienia jednego pracownika. Zamiast tego należą do klasy pracowników jako całości. Powinny być deklarowane jako `static` składowe klasy.

## <a name="example"></a>Przykład

Ten przykład odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika według jednego i wyświetla informacje dotyczące nowego pracownika oraz nową liczbę pracowników. Ten program odczytuje bieżącą liczbę pracowników z klawiatury.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Przykład

Ten przykład pokazuje, że można zainicjować pole `static` przy użyciu innego pola `static`, które nie zostało jeszcze zadeklarowane. Wyniki będą niezdefiniowane, dopóki nie zostanie jawnie przypisana wartość do pola `static`.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
