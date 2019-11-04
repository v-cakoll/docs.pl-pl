---
title: modyfikator statyczny C# -odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: cbd0f6b4ef7976ccc2da2a735ccbba2bf23177e4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422331"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)

Użyj modyfikatora `static`, aby zadeklarować statyczną składową, która należy do samego typu, a nie do określonego obiektu. Modyfikator `static` może być używany z klasami, polami, metodami, właściwościami, operatorami, zdarzeniami i konstruktorami, ale nie można go używać z indeksatorami, finalizatorami ani typami innymi niż klasy. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Przykład

Następująca Klasa jest zadeklarowana jako `static` i zawiera tylko metody `static`:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklaracja stałej lub typu jest niejawnie statycznym elementem członkowskim.

Nie można odwołać się do członka statycznego za pomocą wystąpienia. Zamiast tego odwołuje się do niego za pomocą nazwy typu. Rozważmy na przykład następujące klasy:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Aby odwołać się do statycznego elementu członkowskiego `x`, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`, chyba że element członkowski jest dostępny z tego samego zakresu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Chociaż wystąpienie klasy zawiera oddzielną kopię wszystkich pól wystąpienia klasy, istnieje tylko jedna kopia każdego pola statycznego.

Nie można użyć [tej](this.md) metody do odwoływania się do metod statycznych lub dostępu do właściwości.

Jeśli `static` słowo kluczowe jest stosowane do klasy, wszystkie elementy członkowskie klasy muszą być statyczne.

Klasy i klasy statyczne mogą mieć statyczne konstruktory. Konstruktory statyczne są wywoływane w pewnym momencie od momentu uruchomienia programu i wystąpienia klasy.

> [!NOTE]
> Słowo kluczowe `static` ma więcej ograniczonych użycia niż C++w. Aby porównać ze C++ słowem kluczowym, zobacz [klasyC++magazynu ()](/cpp/cpp/storage-classes-cpp#static).

Aby przedstawić statyczne elementy członkowskie, należy rozważyć klasę, która reprezentuje pracownika firmy. Załóżmy, że Klasa zawiera metodę służącą do policzania pracowników i pola do przechowywania liczby pracowników. Obie metody i pola nie należą do żadnego pracownika wystąpienia. Zamiast tego należy do klasy firmy. W związku z tym powinny być deklarowane jako statyczne elementy członkowskie klasy.

## <a name="example"></a>Przykład

Ten przykład odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika według jednego i wyświetla informacje dotyczące nowego pracownika oraz nową liczbę pracowników. Dla uproszczenia ten program odczytuje bieżącą liczbę pracowników z klawiatury. W prawdziwej aplikacji te informacje powinny być odczytywane z pliku.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Przykład

Ten przykład pokazuje, że chociaż można zainicjować pole statyczne przy użyciu innego pola statycznego, które nie zostało jeszcze zadeklarowane, wyniki będą niezdefiniowane do momentu, gdy jawnie przypiszesz wartość do pola statycznego.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
