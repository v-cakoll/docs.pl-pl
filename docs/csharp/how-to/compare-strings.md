---
title: Jak porównać ciągi - Przewodnik po językach C#
description: Dowiedz się, jak porównywać i porządkować wartości ciągów, z lub bez przypadku, z lub bez kolejności specyficznej dla kultury lub bez niej
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: dda3ec8cb6a0131867e6ea3bb0cf7199d86058ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973321"
---
# <a name="how-to-compare-strings-in-c"></a>Jak porównać ciągi w C\#

Porównujesz ciągi, aby odpowiedzieć na jedno z dwóch pytań: "Czy te dwa ciągi są równe?" lub "W jakiej kolejności należy umieścić te ciągi podczas sortowania?"

Te dwa pytania są skomplikowane przez czynniki, które wpływają na porównania ciągów:

- Możesz wybrać porównanie lub językowe.
- Możesz wybrać, czy sprawa ma znaczenie.
- Można wybrać porównania specyficzne dla kultury.
- Porównania językowe są zależne od kultury i platformy.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Podczas porównywania ciągów definiujesz kolejność między nimi. Porównania są używane do sortowania sekwencji ciągów. Gdy sekwencja jest w znanej kolejności, łatwiej jest wyszukiwać, zarówno dla oprogramowania, jak i dla ludzi. Inne porównania mogą sprawdzić, czy ciągi są takie same. Te kontrole identyczności są podobne do równości, ale niektóre różnice, takie jak różnice w sprawach, mogą być ignorowane.

## <a name="default-ordinal-comparisons"></a>Domyślne porównania pisane

Domyślnie najczęściej zdobytymi operacjami:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>i <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, to jest, [operatorzy `==` równości i `!=` ](../language-reference/operators/equality-operators.md#string-equality), odpowiednio

przeprowadzić porównanie liczba głosów rozróżnianych i, jeśli to konieczne, użyć bieżącej kultury. Poniższy przykład pokazuje, że:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Domyślne porównanie liczba głosów nie uwzględnia reguł językowych podczas porównywania ciągów. Porównuje wartość binarną <xref:System.Char> każdego obiektu w dwóch ciągach. W rezultacie domyślne porównanie liczba głosów jest również rozróżniana.

Należy zauważyć, że <xref:System.String.Equals%2A?displayProperty=nameWithType> test `==` równości `!=` z i operatorów różni <xref:System.String.CompareTo%2A?displayProperty=nameWithType> <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> się od porównania ciągów przy użyciu i metody. Podczas testów równości wykonać porównanie liczba głosów, metody porównania wykonywania porównania z uwzględnieniem wielkości liter, kultury przy użyciu bieżącej kultury. Ponieważ domyślne metody porównania często wykonują różne typy porównań, zaleca się, aby zawsze czyścić intencje kodu, wywołując przeciążenie, które jawnie określa typ porównania do wykonania.

## <a name="case-insensitive-ordinal-comparisons"></a>Porównania z uwzględnieniem wielkości liter

Metoda <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> umożliwia określenie <xref:System.StringComparison> wartości<xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
dla porównania pism niewrażliwych na wielkość liter. Istnieje również metoda <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> statyczna, która wykonuje porównanie liczby głosów bez uwzględniania <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wielkości <xref:System.StringComparison> liter, jeśli określisz wartość dla argumentu. Są one wyświetlane w następującym kodzie:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Podczas wykonywania porównania liczby niewrażliwej na wielkość liter, metody te używają konwencji wielkości liter [kultury niezmiennej.](xref:System.Globalization.CultureInfo.InvariantCulture)

## <a name="linguistic-comparisons"></a>Porównania językowe

Ciągi można również zamówić przy użyciu reguł językowych dla bieżącej kultury.
Jest to czasami określane jako "kolejność sortowania słów". Podczas porównywania językowego niektóre niealfanumeryczne znaki Unicode mogą mieć przypisane specjalne wagi. Na przykład łącznik "-" może mieć przypisaną bardzo małą wagę, dzięki czemu "co-op" i "coop" pojawiają się obok siebie w kolejności sortowania. Ponadto niektóre znaki Unicode mogą być równoważne sekwencji wystąpień. <xref:System.Char> Poniższy przykład używa zwrotu "Tańczą na ulicy". w języku niemieckim z "ss" (U +0073 U + 0073) w jednym ciągu i "ß" (U + 00DF) w innym. Językowo (w systemie Windows) "ss" jest równa niemieckiemu esszetowi: znakowi "ß" zarówno w kulturach "en-US", jak i "de-DE".

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

W tym przykładzie przedstawiono zależności systemu operacyjnego charakter porównań językowych. Hostem interaktywnego okna jest host systemu Linux. Porównania językowe i porządkowe dają takie same wyniki. Jeśli ten sam przykład został uruchomiony na hoście systemu Windows, zobaczysz następujące dane wyjściowe:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

W systemie Windows kolejność sortowania "gliniarza", "coop" i "co-op" zmienia się po zmianie porównania językowego na porównanie porządkowe. Dwa zdania niemieckie również porównują się inaczej, stosując różne typy porównania.

## <a name="comparisons-using-specific-cultures"></a>Porównania z wykorzystaniem określonych kultur

W tym <xref:System.Globalization.CultureInfo> przykładzie przechowuje obiekty dla en-US i de-DE kultur.
Porównania są wykonywane przy <xref:System.Globalization.CultureInfo> użyciu obiektu w celu zapewnienia porównania specyficzne dla kultury.

Zastosowana kultura wpływa na porównania językowe. W poniższym przykładzie przedstawiono wyniki porównywania dwóch zdań niemieckich przy użyciu kultury "en-US" i kultury "de-DE":

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Porównania zależne od kultury są zwykle używane do porównywania i sortowania ciągów wprowadzanych przez użytkowników z innymi ciągami wprowadzanych przez użytkowników. Znaki i konwencje sortowania tych ciągów mogą się różnić w zależności od ustawień regionalnych komputera użytkownika. Nawet ciągi zawierające identyczne znaki mogą sortować inaczej w zależności od kultury bieżącego wątku. Ponadto spróbuj tego przykładowego kodu lokalnie na komputerze z systemem Windows, a otrzymasz następujące wyniki:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Porównania językowe są zależne od bieżącej kultury i są zależne od systemu operacyjnego. Należy wziąć to pod uwagę podczas pracy z porównaniaciągów.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Sortowanie językowe i wyszukiwanie ciągów w tablicach

W poniższych przykładach przedstawiono sposób sortowania i wyszukiwania ciągów w tablicy przy użyciu porównania językowego zależnego od bieżącej kultury. Używasz metod <xref:System.Array> statycznych, <xref:System.StringComparer?displayProperty=nameWithType> które przyjmują parametr.

W tym przykładzie pokazano, jak sortować tablicę ciągów przy użyciu bieżącej kultury:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Po posortowaniu tablicy można wyszukiwać wpisy za pomocą wyszukiwania binarnego. Wyszukiwanie binarne rozpoczyna się w środku kolekcji, aby określić, która połowa kolekcji będzie zawierać poszukiwany ciąg. Każde kolejne porównanie dzieli pozostałą część kolekcji na pół.  Tablica jest sortowana <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>przy użyciu pliku . Funkcja `ShowWhere` lokalna wyświetla informacje o miejscu znalezienia ciągu. Jeśli ciąg nie został znaleziony, zwrócona wartość wskazuje, gdzie byłoby, gdyby zostały znalezione.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Sortowanie i wyszukiwanie święcenia misyjne w kolekcjach

Poniższy kod używa <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy kolekcji do przechowywania ciągów. Ciągi są sortowane <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> przy użyciu metody. Ta metoda wymaga delegata, który porównuje i porządkuje dwa ciągi. Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> zapewnia, że funkcja porównania. Uruchom próbkę i obserwuj kolejność. Ta operacja sortowania używa sortowania z uwzględnieniem wielkości liter. Metody statyczne <xref:System.String.Compare%2A?displayProperty=nameWithType> można użyć do określenia różnych reguł porównania.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po posortowaniu listę ciągów można przeszukiwać za pomocą wyszukiwania binarnego. W poniższym przykładzie pokazano, jak przeszukiwać posortowane wymienione przy użyciu tej samej funkcji porównania. Funkcja `ShowWhere` lokalna pokazuje, gdzie poszukiwany tekst jest lub byłby:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Zawsze upewnij się, że używasz tego samego typu porównania do sortowania i wyszukiwania. Używanie różnych typów porównania do sortowania i wyszukiwania daje nieoczekiwane wyniki.

Klasy kolekcji, <xref:System.Collections.Hashtable?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>takie <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> jak , i konstruktorów, które przyjmują <xref:System.StringComparer?displayProperty=nameWithType> parametr, gdy typ elementów lub kluczy jest `string`. Ogólnie rzecz biorąc należy użyć tych konstruktorów, <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>gdy jest to możliwe i określić albo .

## <a name="reference-equality-and-string-interning"></a>Równość referencyjna i internowanie ciągów

Żadna z próbek <xref:System.Object.ReferenceEquals%2A>nie została wykorzystana. Ta metoda określa, czy dwa ciągi są tego samego obiektu. Może to prowadzić do niespójnych wyników w porównaniaciągów. W poniższym przykładzie przedstawiono funkcję *internowania ciągu* języka C#. Gdy program deklaruje dwie lub więcej identycznych zmiennych ciągu, kompilator przechowuje je wszystkie w tej samej lokalizacji. Wywołując <xref:System.Object.ReferenceEquals%2A> metodę, można zobaczyć, że dwa ciągi faktycznie odnoszą się do tego samego obiektu w pamięci. Użyj <xref:System.String.Copy%2A?displayProperty=nameWithType> metody, aby uniknąć internowania. Po dostosowaniu kopii dwa ciągi mają różne lokalizacje magazynu, mimo że mają tę samą wartość. Uruchom poniższy przykład, aby `a` pokazać, że ciągi i `b` są *internowane,* co oznacza, że mają ten sam magazyn. Ciągi `a` i `c` nie są.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Podczas testowania równości ciągów, należy użyć metod, które jawnie określają, jakiego rodzaju porównania zamierzasz wykonać. Twój kod jest znacznie bardziej wykonalny i czytelny. Użyj przeciążenia metod <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klas, które <xref:System.StringComparison> przyjmują parametr wyliczenia. Można określić typ porównania do wykonania. Należy unikać `==` `!=` używania i operatorów podczas testowania równości. Metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> wystąpienia zawsze wykonywać porównanie z uwzględnieniem wielkości liter. Są one przeznaczone przede wszystkim do porządkowania ciągów alfabetycznie.

Można intern ciąg lub pobrać odwołanie do istniejącego ciągu <xref:System.String.Intern%2A?displayProperty=nameWithType> internowany przez wywołanie metody. Aby ustalić, czy ciąg jest <xref:System.String.IsInterned%2A?displayProperty=nameWithType> internowany, wywołaj metodę.

## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
- [Porównywanie ciągów](../../standard/base-types/comparing.md)
- [Globalizacja i lokalizacja aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)
