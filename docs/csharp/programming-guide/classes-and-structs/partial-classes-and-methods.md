---
title: Częściowe klasy i metody — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399820"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Klasy częściowe i metody (Przewodnik programowania w języku C#)

Istnieje możliwość podzielenia definicji [klasy,](../../language-reference/keywords/class.md) [struktury,](../../language-reference/builtin-types/struct.md) [interfejsu](../../language-reference/keywords/interface.md) lub metody na dwa lub więcej plików źródłowych. Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie części są łączone po skompilowaniu aplikacji.

## <a name="partial-classes"></a>Klasy częściowe

Istnieje kilka sytuacji, gdy dzielenie definicji klasy jest pożądane:

- Podczas pracy nad dużymi projektami rozłożenie klasy na oddzielne pliki umożliwia wielu programistom pracę nad nią w tym samym czasie.

- Podczas pracy z automatycznie generowanym źródłem kod można dodać do klasy bez konieczności ponownego tworzenia pliku źródłowego. Visual Studio używa tej metody, gdy tworzy formularze systemu Windows, kod otoki usługi sieci Web i tak dalej. Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.

- Aby podzielić definicję klasy, użyj modyfikatora [częściowego](../../language-reference/keywords/partial-type.md) słowa kluczowego, jak pokazano poniżej:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Słowo `partial` kluczowe wskazuje, że inne części klasy, struktury lub interfejsu można zdefiniować w przestrzeni nazw. Wszystkie części muszą `partial` używać słowa kluczowego. Wszystkie części muszą być dostępne w czasie kompilacji, aby utworzyć ostateczny typ. Wszystkie części muszą mieć taką samą dostępność, taką jak `public`, `private`, i tak dalej.

Jeśli dowolna część jest zadeklarowana jako abstrakcyjna, cały typ jest uważany za abstrakcyjny. Jeśli jakakolwiek część jest zadeklarowana jako zapieczętowana, cały typ jest uważany za zapieczętowany. Jeśli dowolna część deklaruje typ podstawowy, cały typ dziedziczy tę klasę.

Wszystkie części, które określają klasę podstawową musi zgadzać się, ale części, które pomijają klasę podstawową nadal dziedziczą typ podstawowy. Części można określić różne interfejsy podstawowe, a ostateczny typ implementuje wszystkie interfejsy wymienione przez wszystkie deklaracje częściowe. Wszystkie klasy, struktury lub elementy członkowskie interfejsu zadeklarowane w definicji częściowej są dostępne dla wszystkich innych części. Typ końcowy jest kombinacją wszystkich części w czasie kompilacji.

> [!NOTE]
> Modyfikator `partial` nie jest dostępny na deklaracje delegata lub wyliczenia.

W poniższym przykładzie pokazano, że typy zagnieżdżone mogą być częściowe, nawet jeśli typ, w których są zagnieżdżone, nie jest sam częściowy.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

W czasie kompilacji atrybuty definicji typu częściowego są scalane. Rozważmy na przykład następujące deklaracje:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Są one równoważne następującym deklaracjom:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Ze wszystkich definicji typu częściowego są scalane następujące elementy:

- komentarze XML

- interfejsy

- atrybuty parametrów typu ogólnego

- class — Atrybuty

- elementy członkowskie

Rozważmy na przykład następujące deklaracje:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Są one równoważne następującym deklaracjom:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Ograniczenia

Podczas pracy z definicjami klas częściowych należy przestrzegać kilku reguł:

- Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być modyfikowane za pomocą `partial`. Na przykład następujące deklaracje klas generują błąd:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- `partial` Modyfikator może pojawić się `class`tylko `struct`bezpośrednio `interface`przed słowami kluczowymi , lub .

- Zagnieżdżone typy częściowe są dozwolone w definicjach typu częściowego, jak pokazano w poniższym przykładzie:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Wszystkie definicje typu częściowego, które mają być częściami tego samego typu, muszą być zdefiniowane w tym samym zestawie i tym samym module (plik exe lub dll). Definicje częściowe nie mogą obejmujeć wielu modułów.

- Nazwa klasy i parametry typu ogólnego muszą być zgodne we wszystkich definicjach typu częściowego. Typy ogólne mogą być częściowe. Każda deklaracja częściowa musi używać tych samych nazw parametrów w tej samej kolejności.

- Następujące słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli są obecne w jednej definicji typu częściowego, nie może kolidować ze słowami kluczowymi określonymi w innej definicji częściowej dla tego samego typu:

  - [Publicznego](../../language-reference/keywords/public.md)

  - [Prywatny](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [Wewnętrznego](../../language-reference/keywords/internal.md)

  - [Abstrakcja](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - klasa bazowa

  - [nowy](../../language-reference/keywords/new-modifier.md) modyfikator (zagnieżdżone części)

  - ograniczenia ogólne

Aby uzyskać więcej informacji, zobacz [Ograniczenia parametrów typu](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Przykład 1

### <a name="description"></a>Opis

W poniższym przykładzie pola i konstruktor `Coords`klasy , są zadeklarowane w jednej `PrintCoords`definicji klasy częściowej, a element członkowski , jest zadeklarowany w innej definicji klasy częściowej.

### <a name="code"></a>Code

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Przykład 2

### <a name="description"></a>Opis

W poniższym przykładzie pokazano, że można również opracować częściowe struktury i interfejsy.

### <a name="code"></a>Code

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Metody częściowe

Klasa częściowa lub struktura może zawierać metodę częściową. Jedna część klasy zawiera podpis metody. Opcjonalna implementacja może być zdefiniowana w tej samej części lub innej części. Jeśli implementacja nie jest dostarczana, a następnie metody i wszystkie wywołania metody są usuwane w czasie kompilacji.

Metody częściowe umożliwiają realizatorowi jednej części klasy zdefiniowanie metody, podobnej do zdarzenia. Realizator drugiej części klasy może zdecydować, czy zaimplementować metodę, czy nie. Jeśli metoda nie jest zaimplementowana, kompilator usuwa podpis metody i wszystkie wywołania metody. Wywołania metody, w tym wszystkie wyniki, które mogłyby wystąpić z oceny argumentów w wywołaniach, nie mają wpływu w czasie wykonywania. W związku z tym dowolny kod w klasie częściowej można swobodnie używać metody częściowej, nawet jeśli implementacja nie jest dostarczana. Brak błędów w czasie kompilacji lub w czasie wykonywania spowoduje, jeśli metoda jest wywoływana, ale nie zaimplementowane.

Metody częściowe są szczególnie przydatne jako sposób dostosowywania wygenerowanego kodu. Umożliwiają one nazwę metody i podpis do zarezerwowania, dzięki czemu wygenerowany kod można wywołać metodę, ale deweloper może zdecydować, czy zaimplementować metodę. Podobnie jak klasy częściowe, metody częściowe włączyć kod utworzony przez generator kodu i kod utworzony przez dewelopera ludzkiego do współpracy bez kosztów w czasie wykonywania.

Deklaracja metody częściowej składa się z dwóch części: definicji i implementacji. Mogą one znajdować się w oddzielnych częściach klasy częściowej lub w tej samej części. Jeśli nie ma deklaracji implementacji, kompilator optymalizuje zarówno definiowanie deklaracji i wszystkie wywołania metody.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Częściowe deklaracje metody muszą zaczynać się od kontekstowego słowa kluczowego [częściowego,](../../language-reference/keywords/partial-type.md) a metoda musi zwracać [void](../../language-reference/builtin-types/void.md).

- Metody częściowe mogą mieć [w](../../language-reference/keywords/in-parameter-modifier.md) lub [ref,](../../language-reference/keywords/ref.md) ale nie [obecnie](../../language-reference/keywords/out-parameter-modifier.md) parametrów.

- Metody częściowe są niejawnie [prywatne](../../language-reference/keywords/private.md)i dlatego nie mogą być [wirtualne.](../../language-reference/keywords/virtual.md)

- Metody częściowe nie mogą być [extern](../../language-reference/keywords/extern.md), ponieważ obecność treści określa, czy są one definiowania lub realizacji.

- Metody częściowe mogą mieć [statyczne](../../language-reference/keywords/static.md) i [niebezpieczne](../../language-reference/keywords/unsafe.md) modyfikatory.

- Metody częściowe mogą być ogólne. Ograniczenia są umieszczane na definiowanie deklaracji metody częściowej i opcjonalnie mogą być powtarzane na implementacji jeden. Nazwy parametrów i parametrów typu nie muszą być takie same w deklaracji wykonawczej, jak w definiowaniu.

- Można dokonać [delegata](../../language-reference/builtin-types/reference-types.md) do metody częściowej, który został zdefiniowany i zaimplementowany, ale nie do metody częściowej, która została tylko zdefiniowana.

## <a name="c-language-specification"></a>Specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Typy częściowe](~/_csharplang/spec/classes.md#partial-types) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy](./classes.md)
- [Typy konstrukcji](../../language-reference/builtin-types/struct.md)
- [Interfejsy](../interfaces/index.md)
- [partial (typ)](../../language-reference/keywords/partial-type.md)
