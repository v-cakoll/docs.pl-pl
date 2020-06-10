---
title: Jak porównać ciągi — przewodnik w języku C#
description: Dowiedz się, jak porównywać i zamawiać wartości ciągów, z lub bez wielkości liter, z lub bez określania kolejności specyficznej dla kultury
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: 725441f5399f72b6457af461d51419c35077f4c2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662917"
---
# <a name="how-to-compare-strings-in-c"></a>Jak porównać ciągi w języku C\#

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
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>i <xref:System.String.op_Inequality%2A?displayProperty=nameWithType> , czyli [Operatory równości `==` i `!=` ](../language-reference/operators/equality-operators.md#string-equality), odpowiednio

Wykonaj porównanie porządkowe z uwzględnieniem wielkości liter i, jeśli to konieczne, Użyj bieżącej kultury. Poniższy przykład pokazuje, że:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet1":::

Domyślne porównanie porządkowe nie uwzględnia reguł lingwistycznych podczas porównywania ciągów. Porównuje wartość binarną każdego <xref:System.Char> obiektu w dwóch ciągach. W związku z tym domyślne porównanie porządkowe uwzględnia wielkość liter.

Należy zauważyć, że test równości z <xref:System.String.Equals%2A?displayProperty=nameWithType> i `==` Operatory and `!=` różni się od porównania ciągów przy użyciu <xref:System.String.CompareTo%2A?displayProperty=nameWithType> <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> metod i. Chociaż testy pod kątem równości wykonują porównanie porządkowe z uwzględnieniem wielkości liter, metody porównania wykonują porównanie z uwzględnieniem wielkości liter, z których korzysta bieżąca kultura. Ponieważ domyślne metody porównywania często wykonują różne typy porównań, zalecamy, aby zawsze upewnić się, że zamierzenia kodu jest jasne, wywołując Przeciążenie, które jawnie określa typ porównania do wykonania.

## <a name="case-insensitive-ordinal-comparisons"></a>Porównanie porządkowe bez uwzględniania wielkości liter

<xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType>Metoda pozwala określić <xref:System.StringComparison> wartość<xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
w przypadku porównania porządkowego bez uwzględniania wielkości liter. Istnieje również metoda statyczna <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> , która wykonuje porównanie porządkowe bez uwzględniania wielkości liter, jeśli określono wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> <xref:System.StringComparison> argumentu. Są one wyświetlane w następującym kodzie:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet2":::

W przypadku porównywania liczb porządkowych bez uwzględniania wielkości liter te metody wykorzystują konwencje wielkości liter [kultury niezmiennej](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Porównania lingwistyczne

Ciągi mogą być również uporządkowane przy użyciu reguł lingwistycznych dla bieżącej kultury.
Jest to czasami nazywane "kolejnością sortowania wyrazów". W przypadku przeprowadzania porównania w języku niektóre znaki niealfanumeryczne Unicode mogą mieć przypisane specjalne wagi. Na przykład łącznik "-" może mieć przypisaną bardzo małą wagę, tak aby "współ" i "coop" były widoczne obok siebie w kolejności sortowania. Ponadto niektóre znaki Unicode mogą być równoważne sekwencji <xref:System.Char> wystąpień. Poniższy przykład używa frazy "odpowiedzialna w ulicy". w języku niemieckim z "SS" (U + 0073 U + 0073) w jednym ciągu i "ß" (U + 00DF) w innej. Językowo (w systemie Windows) "SS" jest równa niemieckiej Esszet: "ß" w przypadku kultur "en-US" i "de-DE".

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet3":::

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

Ten przykład przechowuje <xref:System.Globalization.CultureInfo> obiekty dla kultur en-us i de-de.
Porównania są wykonywane przy użyciu <xref:System.Globalization.CultureInfo> obiektu, aby zapewnić porównanie specyficzne dla kultury.

Kultura, która ma wpływ na porównania językowe. Poniższy przykład pokazuje wyniki porównania dwóch zdań niemieckich przy użyciu kultury "pl-US" i kultury "de-DE":

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet4":::

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

W poniższych przykładach pokazano, jak sortować i wyszukiwać ciągi w tablicy przy użyciu porównania językowej zależnej od bieżącej kultury. Używasz <xref:System.Array> metod statycznych przyjmujących <xref:System.StringComparer?displayProperty=nameWithType> parametr.

Ten przykład pokazuje, jak sortować tablicę ciągów przy użyciu bieżącej kultury:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet5":::

Po posortowaniu tablicy można wyszukać wpisy przy użyciu wyszukiwania binarnego. Wyszukiwanie binarne zaczyna się w środku kolekcji, aby określić, która połowa kolekcji będzie zawierać szukany ciąg. Każde kolejne porównanie dzieli pozostałą część kolekcji na pół.  Tablica jest sortowana przy użyciu <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType> . Funkcja lokalna `ShowWhere` wyświetla informacje o miejscu, w którym znaleziono ciąg. Jeśli ciąg nie został odnaleziony, zwrócona wartość wskazuje, gdzie zostanie znaleziona.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet6":::

## <a name="ordinal-sorting-and-searching-in-collections"></a>Sortowanie porządkowe i wyszukiwanie w kolekcjach

Poniższy kod używa <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy kolekcji do przechowywania ciągów. Ciągi są sortowane przy użyciu <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody. Ta metoda wymaga delegata, który porównuje i porządkuje dwa ciągi. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Metoda zapewnia tę funkcję porównania. Uruchom przykład i zaobserwuj zamówienie. Ta operacja sortowania używa sortowania z uwzględnieniem wielkości liter. <xref:System.String.Compare%2A?displayProperty=nameWithType>Aby określić różne reguły porównywania, należy użyć metod statycznych.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet7":::

Po posortowaniu lista ciągów może być wyszukiwana przy użyciu wyszukiwania binarnego. Poniższy przykład pokazuje, jak przeszukiwać posortowane listy przy użyciu tej samej funkcji porównywania. Funkcja lokalna `ShowWhere` pokazuje, gdzie poszukiwany tekst to lub:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet8":::

Zawsze upewnij się, że używasz tego samego typu porównania do sortowania i wyszukiwania. Użycie różnych typów porównania do sortowania i wyszukiwania powoduje utworzenie nieoczekiwanych wyników.

Klasy kolekcji, takie jak <xref:System.Collections.Hashtable?displayProperty=nameWithType> , <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> mają konstruktory przyjmujące <xref:System.StringComparer?displayProperty=nameWithType> parametr, gdy typem elementów lub kluczy jest `string` . Ogólnie rzecz biorąc, należy używać tych konstruktorów, jeśli jest to możliwe, i określić albo <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType> .

## <a name="reference-equality-and-string-interning"></a>Równość odwołania i ciąg InterNIC

Żaden z próbek nie został użyty <xref:System.Object.ReferenceEquals%2A> . Ta metoda określa, czy dwa ciągi są tego samego obiektu. Może to prowadzić do niespójnych wyników w porównaniach ciągów. Poniższy przykład demonstruje funkcję *interniing* w języku C#. Gdy program deklaruje co najmniej dwie identyczne zmienne ciągów, kompilator przechowuje je wszystkie w tej samej lokalizacji. Wywołując <xref:System.Object.ReferenceEquals%2A> metodę, można zobaczyć, że dwa ciągi rzeczywiście odwołują się do tego samego obiektu w pamięci. <xref:System.String.Copy%2A?displayProperty=nameWithType>Aby uniknąć InterNIC, użyj metody. Po wykonaniu kopii te dwa ciągi mają różne lokalizacje przechowywania, nawet jeśli mają tę samą wartość. Uruchom Poniższy przykład, aby wyświetlić te ciągi i o tym, że mają `a` `b` one udział w tym samym magazynie. *interned* Ciągi `a` i `c` nie są.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet9":::

> [!NOTE]
> Podczas testowania pod kątem równości ciągów należy użyć metod, które jawnie określają rodzaj porównania, który ma być wykonywany. Kod jest znacznie bardziej czytelny i możliwy do odczytania. Użyj przeciążenia metod <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klas, które pobierają <xref:System.StringComparison> parametr wyliczeniowy. Należy określić typ porównania do wykonania. Należy unikać używania `==` `!=` operatorów i podczas testowania pod kątem równości. <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Metody wystąpienia zawsze wykonują porządkową wielkość liter. Są one głównie odpowiednie do porządkowania ciągów alfabetycznie.

Można skontaktować się z ciągiem lub pobrać odwołanie do istniejącego ciągu InterNIC, wywołując <xref:System.String.Intern%2A?displayProperty=nameWithType> metodę. Aby określić, czy ciąg jest InterNIC, wywołaj <xref:System.String.IsInterned%2A?displayProperty=nameWithType> metodę.

## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
- [Porównywanie ciągów](../../standard/base-types/comparing.md)
- [Globalizacja i lokalizowanie aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)
