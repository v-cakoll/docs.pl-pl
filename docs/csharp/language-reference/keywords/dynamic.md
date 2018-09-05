---
title: dynamic (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: bddcb8890ef7312047d05794ccef0b638de4ed78
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538430"
---
# <a name="dynamic-c-reference"></a>dynamic (odwołanie w C#)

`dynamic` Typ umożliwia operacje, w których występuje Pomiń sprawdzanie typów w czasie kompilacji. Zamiast tego te operacje są rozwiązywane w czasie wykonywania. `dynamic` Typu upraszcza dostęp do interfejsów API modelu COM, takich jak Office interfejsów API usługi Automation i również dynamiczne interfejsy API, takich jak biblioteki IronPython i do HTML Document Object Model (DOM).

Typ `dynamic` zachowuje się jak typ `object` w większości przypadków. Jednak operacje, które zawierają wyrażenia typu `dynamic` nie są rozpoznawane lub typ sprawdzana przez kompilator. Pakiety kompilatora, które razem informacje na temat operacji, a te informacje później użyte do oceny operacji w czasie wykonywania. W ramach procesu, a zmienne typu `dynamic` są kompilowane do zmiennych typu `object`. W związku z tym, wpisz `dynamic` istnieje tylko w czasie kompilacji, nie w czasie wykonywania.

Poniższy przykład zachowanie różni się od zmiennej typu `dynamic` do zmiennej typu `object`. Aby sprawdzić typ każdej zmiennej w czasie kompilacji, umieść wskaźnik myszy nad `dyn` lub `obj` w `WriteLine` instrukcji. Funkcja IntelliSense pokazuje **dynamiczne** dla `dyn` i **obiektu** dla `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

`WriteLine` Instrukcji prezentuje typy środowiska wykonawczego `dyn` i `obj`. W tym momencie mają ten sam typ, liczbę całkowitą. Są następujące wyniki:

`System.Int32`

`System.Int32`

Aby zobaczyć różnicę między `dyn` i `obj` w czasie kompilacji, Dodaj następujące dwa wiersze między deklaracjami i `WriteLine` instrukcji w poprzednim przykładzie.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Błąd kompilatora jest zgłaszany, próba dodanie całkowitą, a obiekt w wyrażeniu `obj + 3`. Jednak błąd nie jest zgłaszany, `dyn + 3`. Wyrażenie, które zawiera `dyn` nie jest sprawdzana w czasie kompilacji, ponieważ typ `dyn` jest `dynamic`.

## <a name="context"></a>Kontekst

`dynamic` — Słowo kluczowe może znajdować się bezpośrednio lub jako składnik skonstruowanego typu w następujących sytuacjach:

- W deklaracjach typu właściwości, pola, indeksowanie, parametr zwracają wartość, zmienna lokalna lub typ ograniczenia. Następujące klasy definicja używa `dynamic` w kilku różnych deklaracji.

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- W jawnych konwersji typów, jako typ docelowy konwersji.

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- W dowolnym kontekście, gdy typy służyć jako wartości, takich jak na prawej krawędzi `is` operatora lub `as` operatora, lub jako argument `typeof` jako część skonstruowanego typu. Na przykład `dynamic` mogą być używane w następujących wyrażeń.

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `dynamic` w kilka deklaracji. `Main` Metoda również zachowanie różni się od typu w czasie kompilacji sprawdzania ze sprawdzaniem typu run-time.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [object](../../../csharp/language-reference/keywords/object.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [as](../../../csharp/language-reference/keywords/as.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
- [Instrukcje: bezpieczne rzutowanie za pomocą operatorów as i is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
- [Wskazówki: Tworzenie obiektów dynamicznych i posługiwanie](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
