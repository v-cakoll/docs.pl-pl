---
title: 'Instrukcje: Porównywanie ciągów- C# Przewodnik'
description: Dowiedz się, jak porównywać i zamawiać wartości ciągów, z lub bez wielkości liter, z lub bez określania kolejności specyficznej dla kultury
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: a3e5f8dd9cfac809aafc2533463390cd5a64e0d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395454"
---
# <a name="how-to-compare-strings-in-c"></a>Jak porównać ciągi w języku C @ no__t-0

Można porównać ciągi, aby odpowiedzieć na jedno z dwóch pytań: "czy te dwa ciągi są równe?" lub "w jakiej kolejności te ciągi mają być umieszczane podczas sortowania?"

Te dwa pytania są skomplikowane przez czynniki wpływające na porównania ciągów:

- Można wybrać porównanie porządkowe lub językowe.
- Możesz wybrać opcję jeśli sprawa ma znaczenie.
- Można wybrać porównania specyficzne dla kultury.
- Porównania językowe są zależne od kultury i platformy.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Podczas porównywania ciągów należy zdefiniować kolejność między nimi. Porównania są używane do sortowania sekwencji ciągów. Gdy sekwencja jest w znanej kolejności, łatwiejsze wyszukiwanie, zarówno w przypadku oprogramowania, jak i dla ludzi. Inne porównania mogą sprawdzić, czy ciągi są takie same. Te same kontrole są podobne do równość, ale niektóre różnice, takie jak różnice wielkości liter, mogą zostać zignorowane.

## <a name="default-ordinal-comparisons"></a>Domyślne porównania porządkowe

Domyślnie najbardziej typowe operacje:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType> i <xref:System.String.op_Inequality%2A?displayProperty=nameWithType>, czyli [Operatory równości `==` i `!=`](../language-reference/operators/equality-operators.md#string-equality)odpowiednio

Wykonaj porównanie porządkowe z uwzględnieniem wielkości liter i, jeśli to konieczne, Użyj bieżącej kultury. Poniższy przykład pokazuje, że:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Domyślne porównanie porządkowe nie uwzględnia reguł lingwistycznych podczas porównywania ciągów. Porównuje wartość binarną każdego obiektu <xref:System.Char> w dwóch ciągach. W związku z tym domyślne porównanie porządkowe uwzględnia wielkość liter.

Należy zauważyć, że test dla równości z <xref:System.String.Equals%2A?displayProperty=nameWithType> i operatory `==` i `!=` różnią się od porównania ciągów przy użyciu metod <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)>. Chociaż testy pod kątem równości wykonują porównanie porządkowe z uwzględnieniem wielkości liter, metody porównania wykonują porównanie z uwzględnieniem wielkości liter, z których korzysta bieżąca kultura. Ponieważ domyślne metody porównywania często wykonują różne typy porównań, zalecamy, aby zawsze upewnić się, że zamierzenia kodu jest jasne, wywołując Przeciążenie, które jawnie określa typ porównania do wykonania.

## <a name="case-insensitive-ordinal-comparisons"></a>Porównanie porządkowe bez uwzględniania wielkości liter

Metoda <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> umożliwia określenie <xref:System.StringComparison> wartości <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
w przypadku porównania porządkowego bez uwzględniania wielkości liter. Istnieje również statyczna metoda <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType>, która wykonuje porównanie porządkowe bez uwzględniania wielkości liter, jeśli dla argumentu <xref:System.StringComparison> określono wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>. Są one wyświetlane w następującym kodzie:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

W przypadku porównywania liczb porządkowych bez uwzględniania wielkości liter te metody wykorzystują konwencje wielkości liter [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Porównania lingwistyczne

Ciągi mogą być również uporządkowane przy użyciu reguł lingwistycznych dla bieżącej kultury.
Jest to czasami nazywane "kolejnością sortowania wyrazów". W przypadku przeprowadzania porównania w języku niektóre znaki niealfanumeryczne Unicode mogą mieć przypisane specjalne wagi. Na przykład łącznik "-" może mieć przypisaną bardzo małą wagę, tak aby "współ" i "coop" były widoczne obok siebie w kolejności sortowania. Ponadto niektóre znaki Unicode mogą być równoważne sekwencji wystąpień <xref:System.Char>. Poniższy przykład używa frazy "odpowiedzialna w ulicy". w języku niemieckim z "SS" (U + 0073 U + 0073) w jednym ciągu i "ß" (U + 00DF) w innej. Językowo (w systemie Windows) "SS" jest równa niemieckiej Esszet: "ß" w przypadku kultur "en-US" i "de-DE".

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

W tym przykładzie przedstawiono charakter porównania językowe zależne od systemu operacyjnego. Host dla okna interaktywnego jest hostem systemu Linux. Porównania lingwistyczne i porządkowe dają te same wyniki. Jeśli ten sam przykład został uruchomiony na hoście z systemem Windows, zobaczysz następujące dane wyjściowe:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

W systemie Windows kolejność sortowania "COP", "coop" i "współ-op" zmienia się w przypadku zmiany języka w porównaniu z porównaniem do liczby porządkowej. Dwa zdania niemiecki są również porównywane inaczej przy użyciu różnych typów porównania.

## <a name="comparisons-using-specific-cultures"></a>Porównania przy użyciu określonych kultur

Ten przykład przechowuje <xref:System.Globalization.CultureInfo> obiektów dla kultur en-US i de-DE.
Porównania są wykonywane przy użyciu obiektu <xref:System.Globalization.CultureInfo> w celu zapewnienia porównania specyficznego dla kultury.

Kultura, która ma wpływ na porównania językowe. Poniższy przykład pokazuje wyniki porównania dwóch zdań niemieckich przy użyciu kultury "pl-US" i kultury "de-DE":

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Porównania wrażliwe na kulturę są zwykle używane do porównywania i sortowania ciągów wejściowych przez użytkowników z innymi ciągami wejściowymi przez użytkowników. Znaki i konwencje sortowania tych ciągów mogą się różnić w zależności od ustawień regionalnych komputera użytkownika. Nawet ciągi zawierające identyczne znaki mogą być sortowane w różny sposób w zależności od kultury bieżącego wątku. Dodatkowo Wypróbuj ten przykładowy kod lokalnie na komputerze z systemem Windows i uzyskasz następujące wyniki:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Porównania językowe są zależne od bieżącej kultury i są zależne od systemu operacyjnego. Należy wziąć pod uwagę podczas pracy z porównaniami ciągów.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Sortowanie lingwistyczne i wyszukiwanie ciągów w tablicach

W poniższych przykładach pokazano, jak sortować i wyszukiwać ciągi w tablicy przy użyciu porównania językowej zależnej od bieżącej kultury. Używasz statycznych metod <xref:System.Array>, które pobierają parametr <xref:System.StringComparer?displayProperty=nameWithType>.

Ten przykład pokazuje, jak sortować tablicę ciągów przy użyciu bieżącej kultury:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Po posortowaniu tablicy można wyszukać wpisy przy użyciu wyszukiwania binarnego. Wyszukiwanie binarne zaczyna się w środku kolekcji, aby określić, która połowa kolekcji będzie zawierać szukany ciąg. Każde kolejne porównanie dzieli pozostałą część kolekcji na pół.  Tablica jest sortowana przy użyciu <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Funkcja lokalna `ShowWhere` wyświetla informacje o tym, gdzie znaleziono ciąg. Jeśli ciąg nie został odnaleziony, zwrócona wartość wskazuje, gdzie zostanie znaleziona.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Sortowanie porządkowe i wyszukiwanie w kolekcjach

Poniższy kod używa klasy kolekcji <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> do przechowywania ciągów. Ciągi są sortowane przy użyciu metody <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Ta metoda wymaga delegata, który porównuje i porządkuje dwa ciągi. Metoda <xref:System.String.CompareTo%2A?displayProperty=nameWithType> zapewnia tę funkcję porównania. Uruchom przykład i zaobserwuj zamówienie. Ta operacja sortowania używa sortowania z uwzględnieniem wielkości liter. Aby określić różne reguły porównywania, należy użyć statycznych metod <xref:System.String.Compare%2A?displayProperty=nameWithType>.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po posortowaniu lista ciągów może być wyszukiwana przy użyciu wyszukiwania binarnego. Poniższy przykład pokazuje, jak przeszukiwać posortowane listy przy użyciu tej samej funkcji porównywania. Funkcja lokalna `ShowWhere` pokazuje, gdzie poszukiwany tekst to lub:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Zawsze upewnij się, że używasz tego samego typu porównania do sortowania i wyszukiwania. Użycie różnych typów porównania do sortowania i wyszukiwania powoduje utworzenie nieoczekiwanych wyników.

Klasy kolekcji, takie jak <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> mają konstruktory przyjmujące <xref:System.StringComparer?displayProperty=nameWithType> parametr, gdy typ elementów lub kluczy jest `string`. Ogólnie rzecz biorąc, należy używać tych konstruktorów, jeśli jest to możliwe, i określić wartość <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Równość odwołania i ciąg InterNIC

Żadna z próbek nie została użyta <xref:System.Object.ReferenceEquals%2A>. Ta metoda określa, czy dwa ciągi są tego samego obiektu. Może to prowadzić do niespójnych wyników w porównaniach ciągów. Poniższy przykład demonstruje funkcję *InterNIC* C#. Gdy program deklaruje co najmniej dwie identyczne zmienne ciągów, kompilator przechowuje je wszystkie w tej samej lokalizacji. Wywołując metodę <xref:System.Object.ReferenceEquals%2A>, można zobaczyć, że dwa ciągi rzeczywiście odwołują się do tego samego obiektu w pamięci. Aby uniknąć InterNIC, użyj metody <xref:System.String.Copy%2A?displayProperty=nameWithType>. Po wykonaniu kopii te dwa ciągi mają różne lokalizacje przechowywania, nawet jeśli mają tę samą wartość. Uruchom Poniższy przykład, aby pokazać, że ciągi `a` i `b` są *InterNIC* , że korzystają z tego samego magazynu. Ciągi `a` i `c` nie są.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Podczas testowania pod kątem równości ciągów należy użyć metod, które jawnie określają rodzaj porównania, który ma być wykonywany. Kod jest znacznie bardziej czytelny i możliwy do odczytania. Użyj przeciążeń metod <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType>, które pobierają parametr wyliczenia <xref:System.StringComparison>. Należy określić typ porównania do wykonania. Unikaj używania operatorów `==` i `!=` podczas testowania pod kątem równości. Metody wystąpienia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> zawsze wykonują porządkową wielkość liter. Są one głównie odpowiednie do porządkowania ciągów alfabetycznie.

Można skontaktować się z ciągiem lub pobrać odwołanie do istniejącego ciągu InterNIC, wywołując metodę <xref:System.String.Intern%2A?displayProperty=nameWithType>. Aby określić, czy ciąg jest InterNIC, wywołaj metodę <xref:System.String.IsInterned%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
- [Porównywanie ciągów](../../standard/base-types/comparing.md)
- [Globalizowanie i lokalizowanie aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)
