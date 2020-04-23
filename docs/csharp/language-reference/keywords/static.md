---
title: modyfikator statyczny — odwołanie do języka C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102063"
---
# <a name="static-c-reference"></a>static (odwołanie w C#)

Ta strona `static` zawiera słowo kluczowe modyfikatora. Słowo `static` kluczowe jest również [`using static`](using-static.md) częścią dyrektywy.

Użyj `static` modyfikatora do deklarowania statycznego elementu członkowskiego, który należy do samego typu, a nie do określonego obiektu. Modyfikator `static` może służyć `static` do deklarowania klas. W klasach, interfejsach i strukturach można `static` dodać modyfikator do pól, metod, właściwości, operatorów, zdarzeń i konstruktorów. Modyfikator `static` nie może być używany z indeksatorów lub finalizatorów. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i Elementy członkowskie klasy statycznej](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example---static-class"></a>Przykład - klasa statyczna

Następująca klasa jest `static` zadeklarowana `static` jako i zawiera tylko metody:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Deklaracja stała lub typ `static` jest niejawnie elementem członkowskim. Nie `static` można odwoływać się do elementu członkowskiego za pośrednictwem wystąpienia. Zamiast tego odwołuje się do nazwy typu. Rozważmy na przykład następującą klasę:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Aby odwołać `static` `x`się do elementu członkowskiego, użyj w pełni kwalifikowanej nazwy, `MyBaseC.MyStruct.x`chyba że element członkowski jest dostępny z tego samego zakresu:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Podczas gdy wystąpienie klasy zawiera oddzielną kopię wszystkich pól instancji klasy, istnieje `static` tylko jedna kopia każdego pola.

Nie można użyć [`this`](this.md) do odwoływania się `static` do metod lub akcesorów właściwości.

Jeśli `static` słowo kluczowe jest stosowane do klasy, wszyscy członkowie `static`klasy muszą być .

Klasy, interfejsy `static` i klasy `static` mogą mieć konstruktory. Konstruktor `static` jest wywoływany w pewnym momencie między uruchomieniem programu i wystąpienia klasy.

> [!NOTE]
> Słowo `static` kluczowe ma bardziej ograniczone zastosowania niż w języku C++. Aby porównać je ze słowem kluczowym C++, zobacz [Klasy magazynu (C++)](/cpp/cpp/storage-classes-cpp#static).

Aby `static` zademonstrować członków, należy wziąć pod uwagę klasę, która reprezentuje pracownika firmy. Załóżmy, że klasa zawiera metodę liczenia pracowników i pole do przechowywania liczby pracowników. Zarówno metoda, jak i pole nie należą do żadnego wystąpienia pracownika. Zamiast tego należą do klasy pracowników jako całości. Powinny one być `static` zadeklarowane jako członkowie klasy.

## <a name="example---static-field-and-method"></a>Przykład — pole statyczne i metoda

W tym przykładzie odczytuje nazwę i identyfikator nowego pracownika, zwiększa licznik pracownika o jeden i wyświetla informacje dla nowego pracownika i nową liczbę pracowników. Ten program odczytuje bieżącą liczbę pracowników z klawiatury.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Przykład - inicjowanie statyczne

W tym przykładzie pokazano, `static` że można `static` zainicjować pole przy użyciu innego pola, które nie zostało jeszcze zadeklarowane. Wyniki będą niezdefiniowane, dopóki nie zostanie `static` jawnie przypisana wartość do pola.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [Modyfikatory](index.md)
- [przy użyciu dyrektywy statycznej](using-static.md)
- [Klasy statyczne i statyczni członkowie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
