---
title: Klasy częściowe i metody — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: e359913aad4b8cea001a894d4ba5720fab54d42b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451918"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Klasy częściowe i metody (Przewodnik programowania w języku C#)

Istnieje możliwość podziału definicji [klasy](../../language-reference/keywords/class.md), [struktury](../../language-reference/keywords/struct.md), [interfejsu](../../language-reference/keywords/interface.md) lub metody na więcej niż dwa pliki źródłowe. Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie części są łączone podczas kompilowania aplikacji.

## <a name="partial-classes"></a>Klasy częściowe

Istnieje kilka sytuacji, w których pożądana jest podział definicji klasy:

- Podczas pracy nad dużymi projektami rozłożenie klasy na osobne pliki umożliwia wielu programistom jednoczesną pracę nad nią.

- Podczas pracy z automatycznie generowanym źródłem kod można dodać do klasy bez konieczności ponownego tworzenia pliku źródłowego. Program Visual Studio używa tego podejścia, gdy tworzy Windows Forms, kod otoki usługi sieci Web i tak dalej. Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.

- Aby podzielić definicję klasy, użyj modyfikatora [częściowego](../../language-reference/keywords/partial-type.md) słowa kluczowego, jak pokazano poniżej:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Słowo kluczowe `partial` wskazuje, że w przestrzeni nazw można definiować inne części klasy, struktury lub interfejsu. Wszystkie części muszą używać słowa kluczowego `partial`. Wszystkie części muszą być dostępne w czasie kompilacji w celu utworzenia typu końcowego. Wszystkie części muszą mieć taką samą dostępność, jak `public`, `private`i tak dalej.

Jeśli jakakolwiek część jest zadeklarowana jako abstract, cały typ jest uznawany za abstrakcyjny. Jeśli jakakolwiek część jest zadeklarowana jako Sealed, cały typ jest uznawany za zapieczętowany. Jeśli jakakolwiek część deklaruje typ podstawowy, cały typ dziedziczy tę klasę.

Wszystkie części określające klasę bazową muszą wyrazić zgodę, ale części, które pomijają klasę bazową, nadal dziedziczą typ podstawowy. Części mogą określać różne interfejsy podstawowe, a końcowy typ implementuje wszystkie interfejsy wymienione przez wszystkie częściowe deklaracje. Każdy element członkowski klasy, struktury lub interfejsu zadeklarowany w częściowej definicji jest dostępny dla wszystkich innych części. Ostatni typ to kombinacja wszystkich części w czasie kompilacji.

> [!NOTE]
> Modyfikator `partial` nie jest dostępny w deklaracjach delegata ani wyliczania.

Poniższy przykład pokazuje, że zagnieżdżone typy mogą być częścią, nawet jeśli typ, w którym są zagnieżdżone, nie jest częścią.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

W czasie kompilacji atrybuty częściowych definicji typu są scalane. Rozważmy na przykład następujące deklaracje:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Są one równoważne z następującymi deklaracjami:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Następujące elementy zostały scalone ze wszystkich definicji typów częściowych:

- komentarze XML

- interfejsy

- atrybuty parametru typu ogólnego

- class — Atrybuty

- elementy członkowskie

Rozważmy na przykład następujące deklaracje:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Są one równoważne z następującymi deklaracjami:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Ograniczenia

Istnieje kilka reguł, które należy wykonać podczas pracy ze częściowymi definicjami klas:

- Wszystkie definicje typu częściowego, które powinny być częściami tego samego typu, muszą być modyfikowane przy użyciu `partial`. Na przykład następujące deklaracje klas generują błąd:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- Modyfikator `partial` może występować tylko bezpośrednio przed słowami kluczowymi `class`, `struct`lub `interface`.

- Zagnieżdżone typy częściowe są dozwolone w definicjach typów częściowych, jak pokazano w następującym przykładzie:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być zdefiniowane w tym samym zestawie i w tym samym module (pliku exe lub. dll). Definicje częściowe nie mogą obejmować wielu modułów.

- Parametry nazwy klasy i typu ogólnego muszą być zgodne ze wszystkimi definicjami częściowych typów. Typy ogólne mogą być częściowe. Każda deklaracja częściowa musi używać tych samych nazw parametrów w tej samej kolejności.

- Następujące słowa kluczowe w definicji częściowej typu są opcjonalne, ale jeśli są obecne w jednej definicji częściowej, nie mogą powodować konfliktu ze słowami kluczowymi określonymi w innej definicji częściowej dla tego samego typu:

  - [public](../../language-reference/keywords/public.md)

  - [private](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [internal](../../language-reference/keywords/internal.md)

  - [abstract](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - klasa bazowa

  - [New](../../language-reference/keywords/new-modifier.md) — modyfikator (części zagnieżdżone)

  - Ograniczenia ogólne

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Przykład 1

### <a name="description"></a>Opis

W poniższym przykładzie pola i Konstruktor klasy, `Coords`, są zadeklarowane w jednej częściowej definicji klasy, a element członkowski, `PrintCoords`, jest zadeklarowany w innej definicji klasy częściowej.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Przykład 2

### <a name="description"></a>Opis

Poniższy przykład pokazuje, że można również opracowywać częściowe struktury i interfejsy.

### <a name="code"></a>Kod

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Metody częściowe

Częściowa Klasa lub struktura mogą zawierać metodę częściową. Jedna część klasy zawiera podpis metody. Opcjonalna implementacja może być zdefiniowana w tej samej części lub innej części. Jeśli implementacja nie zostanie podana, Metoda i wszystkie wywołania metody są usuwane w czasie kompilacji.

Metody częściowe umożliwiają implementowanie jednej części klasy w celu zdefiniowania metody, podobnej do zdarzenia. Realizator drugiej części klasy może zdecydować, czy zaimplementować metodę, czy nie. Jeśli metoda nie jest zaimplementowana, kompilator usuwa sygnaturę metody i wszystkie wywołania metody. Wywołania metody, w tym wszelkie wyniki, które byłyby wynikiem oceny argumentów w wywołaniach, nie mają wpływu w czasie wykonywania. W związku z tym, każdy kod w klasie częściowej może swobodnie korzystać z metody częściowej, nawet jeśli implementacja nie została podana. Jeśli metoda zostanie wywołana, ale nie została zaimplementowana, nie zostaną wykryte błędy w czasie kompilacji ani w czasie wykonywania.

Metody częściowe są szczególnie przydatne jako sposób dostosowywania wygenerowanego kodu. Umożliwiają one zarezerwowanie nazwy metody i podpisu, aby wygenerowany kod mógł wywołać metodę, ale deweloper może zdecydować, czy zaimplementować metodę. Podobnie jak klasy częściowe, metody częściowe umożliwiają kod utworzony przez generator kodu i kod utworzony przez dewelopera ludzkiego do pracy bez kosztów w czasie wykonywania.

Deklaracja metody częściowej składa się z dwóch części: definicji i implementacji. Mogą one znajdować się w osobnych częściach klasy częściowej lub w tej samej części. W przypadku braku deklaracji implementacji kompilator optymalizuje zarówno deklarację definiującą, jak i wszystkie wywołania metody.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Deklaracje metody częściowej muszą zaczynać się od kontekstowego słowa kluczowego [częściowego](../../language-reference/keywords/partial-type.md) , a metoda musi zwracać [typ void](../../language-reference/builtin-types/void.md).

- Metody częściowe mogą mieć parametry [in](../../language-reference/keywords/in-parameter-modifier.md) lub [ref](../../language-reference/keywords/ref.md) , ale nie [out](../../language-reference/keywords/out-parameter-modifier.md) .

- Metody częściowe są niejawnie [prywatne](../../language-reference/keywords/private.md)i dlatego nie mogą być [wirtualne](../../language-reference/keywords/virtual.md).

- Metody częściowe nie mogą być [extern](../../language-reference/keywords/extern.md), ponieważ obecność treści określa, czy są one definiowane lub implementowane.

- Metody częściowe mogą mieć Modyfikatory [static](../../language-reference/keywords/static.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) .

- Metody częściowe mogą być ogólne. Ograniczenia są umieszczane w deklaracji metody częściowej i opcjonalnie mogą być powtórzone na implementującej ją. Nazwy parametrów parametrów i typów nie muszą być takie same w deklaracji implementującej, jak w definicji.

- Można utworzyć [Delegat](../../language-reference/builtin-types/reference-types.md) do metody częściowej, która została zdefiniowana i zaimplementowana, ale nie do metody częściowej, która została zdefiniowana tylko.

## <a name="c-language-specification"></a>Specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typy częściowe](~/_csharplang/spec/classes.md#partial-types) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy](./classes.md)
- [Struktury](./structs.md)
- [Interfejsy](../interfaces/index.md)
- [partial (typ)](../../language-reference/keywords/partial-type.md)
