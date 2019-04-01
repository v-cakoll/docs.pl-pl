---
title: 'Instrukcje: Porównywanie ciągów - C# przewodnik'
description: Dowiedz się, jak porównywanie i kolejność wartości ciągu, z lub bez niego z lub bez kultury określonej kolejności, w przypadku
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: bce234ca3a86f057ec35e1c53d22169ee29b7b94
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58759875"
---
# <a name="how-to-compare-strings-in-c"></a>Sposób porównywania ciągów w języku C\#

Można porównać ciągi odpowiedzi na jedno z dwóch pytań: "Czy te dwa ciągi równy?" lub "W jakiej kolejności tych ciągów będzie umieszczona podczas sortowania ich?"

Czynniki mające wpływ na porównania ciągów są skomplikowany te dwa pytania:

- Możesz wybrać porównania porządkowego lub językową.
- Możesz wybrać, jeśli przypadek ma znaczenie.
- Możesz wybrać właściwe dla kultury porównań.
- Porównania są kultury i zależnych od platformy.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Podczas porównywania ciągów należy zdefiniować kolejność między nimi. Porównania są używane do sortowania sekwencji ciągów. Po sekwencję w kolejności znanych łatwiej wyszukiwać, zarówno w zakresie oprogramowania oraz ludzi. Pozostałych porównań może sprawdzić, czy ciągi są takie same. Te sprawdzenia symetryczność są podobne do porównania, ale niektóre różnice, takie jak wielkość różnic, można zignorować.

## <a name="default-ordinal-comparisons"></a>Porównania liczb porządkowych domyślne

Najbardziej typowe operacje:

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType> 

Użyj porównania porządkowego porównania uwzględniającego wielkość liter, a używają bieżącej kultury. Wyniki są wyświetlane w następującym przykładzie:

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

Porównanie porządkowe nie przyjmuje językowej domyślne zasady pod uwagę podczas porównywania ciągów. Porównuje wartość binarną każdego <xref:System.Char> obiektu w dwóch ciągów. W wyniku porównania porządkowego domyślna jest również wielkość liter. 

Należy pamiętać, że test pod kątem równości z <xref:System.String.Equals%2A?displayProperty=nameWithType> i <xref:System.String.op_Equality%2A?displayProperty=nameWithType> różni się od za pomocą porównania ciągu <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> metody. Podczas testów pod kątem równości wykonać liter porównanie porządkowe, metodę porównywania wykonać porównanie uwzględniającą wielkość liter, wrażliwość na ustawienia kulturowe przy użyciu bieżącej kultury. Ponieważ domyślne metody porównania często wykonywanie różnych rodzajów porównań, zalecamy zawsze tworzyć celem kod czyszczenia, wywołując przeciążenie, które jawnie określa typ porównania do wykonania.

## <a name="case-insensitive-ordinal-comparisons"></a>Porównania liczb porządkowych bez uwzględniania wielkości liter

<xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> Metody umożliwia określenie <xref:System.StringComparison> wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
Porównanie porządkowe bez uwzględniania wielkości liter. Również jest element statyczny <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> metodę, która wykonuje porównania bez uwzględniania porządkowe, jeśli określona wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dla <xref:System.StringComparison> argumentu. Są one wyświetlane w poniższym kodzie:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

Podczas przeprowadzania porównania bez uwzględniania porządkowe, metody te za pomocą Konwencji obudowy [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Porównania

Ciągi również może zostać określona za pomocą reguł językowej dla bieżącej kultury.
To jest czasami określane jako "kolejność sortowania słowo". Podczas wykonywania lingwistyczne porównanie, niektóre znaki niealfanumeryczne Unicode mogą mieć specjalnie przypisane wagi. Na przykład łącznik "-" może być bardzo małą wagę, przypisane do niego "zawiera" i "coop" będą wyświetlane obok siebie w kolejności sortowania. Ponadto niektóre znaki Unicode mogą być odpowiednikiem sekwencji <xref:System.Char> wystąpień. W poniższym przykładzie użyto frazę "One za na ulicy." w języku niemieckim (U + 0073 U + 0073) w jednym ciągu "ss" i "ß" (U + 00DF) w innym. Językowo (w Windows), "ss" jest równy Esszet niemiecki: znak "ß" w "en US" i "de-DE" kultur.

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

Niniejszy przykład pokazuje charakter porównań lingwistycznych zależnym od systemu operacyjnego. Host dla okno interaktywne to hoście z systemem Linux. Analiza językowa i porządkowego porównania działają tak samo. Po uruchomieniu tej samej próbki na hoście Windows będzie widoczne następujące wyniki:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Windows, kolejność sortowania "Kopiuj", "coop" oraz "co-OP będą" Zmień na gdy zmienią się z porównania lingwistyczne porównanie porządkowe. Dwa zdania niemieckiego również porównać różnie przy użyciu typów porównanie różnych.

## <a name="comparisons-using-specific-cultures"></a>Porównania przy użyciu określonych kultur

W tym przykładzie przechowuje <xref:System.Globalization.CultureInfo> obiektów dla kultury en US i de-DE.
Porównania są wykonywane przy użyciu <xref:System.Globalization.CultureInfo> obiektu w celu zapewnienia porównania specyficzne dla kultury.

Kultury, używane dotyczy porównań lingwistycznych. Poniższy przykład przedstawia wyniki porównując dwa zdania niemieckiego przy użyciu kultury "en US" i "de-DE" kultura:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Zależne od kultury porównań są zwykle używane do porównywania i sortowania ciągów w danych wejściowych przez użytkowników z innymi ciągami, danych wejściowych przez użytkowników. Znaki i konwencji sortowania te ciągi mogą się różnić w zależności od ustawień regionalnych komputera użytkownika. Nawet ciągi, które zawierają identyczne znaki mogą sortować inaczej w zależności od kultury bieżącego wątku. Ponadto, wypróbuj ten przykładowy kod lokalnie na komputerze Windows, i zostaną następujące wyniki:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Porównania są zależne od bieżącej kultury i są zależne systemu operacyjnego. Należy wykonać, pod uwagę podczas pracy z porównania ciągów.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Językowej wyszukiwania i sortowania ciągów w tablicach

W poniższych przykładach pokazano, jak sortować i wyszukiwać ciągi w tablicy przy użyciu lingwistyczne porównanie zależne od bieżącej kultury. Używa się statycznej <xref:System.Array> metod, które przyjmują <xref:System.StringComparer?displayProperty=nameWithType> parametru.

W tym przykładzie pokazano, jak do posortowania tablicy ciągów przy użyciu bieżącej kultury:

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Gdy tablica jest posortowana, możesz wyszukać wpisów za pomocą wyszukiwania binarnego. Binarny wyszukiwanie rozpoczyna się w środku kolekcji, aby określić, w którym połowa kolekcja będzie zawierać ciąg używanych. Każde kolejne porównanie dzieli pozostała część kolekcji o połowę.  Tablica jest posortowana przy użyciu <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Funkcja lokalna `ShowWhere` Wyświetla informacje o którym ten ciąg został znaleziony. Jeśli ciąg nie został znaleziony, zwracana wartość wskazuje, gdzie będzie, jeśli je znaleziono.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>Porządkowe sortowanie i wyszukiwanie w kolekcjach

Poniższy kod używa <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy kolekcji do przechowywania ciągów. Ciągi są sortowane przy użyciu <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody. Ta metoda musi mieć obiekt delegowany, porównywania i porządkowania dwa ciągi. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda zapewnia tę funkcję porównywania. Uruchamianie aplikacji przykładowej i obserwuj kolejności. Ta operacja sortowania korzysta z uwzględnieniem wielkości liter sortowania porządkowego. Używa się statycznej <xref:System.String.Compare%2A?displayProperty=nameWithType> określenie reguł porównania różnych metod.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po sortować listę ciągów można przeszukiwać za pomocą wyszukiwania binarnego. Poniższy przykład pokazuje sposób wyszukiwania sortowany wyświetlane przy użyciu tych samych funkcji porównywania. Funkcja lokalna `ShowWhere` pokazuje, gdzie lub byłoby używanych tekstu:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Zawsze upewnij się, że ten sam typ porównania na użytek wyszukiwania i sortowania. Przy użyciu porównanie różnych typów, do sortowania i wyszukiwania daje nieoczekiwane wyniki.

Klasy kolekcji, takie jak <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma konstruktorów przyjmujących <xref:System.StringComparer?displayProperty=nameWithType> parametr, gdy typ elementów i kluczy to `string`. Ogólnie rzecz biorąc, należy używać tych konstruktorów, jeśli to możliwe oraz określ <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Równość odniesienia i wewnętrzne przygotowanie ciągu

Brak próbek używanych <xref:System.Object.ReferenceEquals%2A>. Ta metoda określa, czy dwa ciągi są tego samego obiektu. Może to prowadzić do niespójnych wyników w porównaniach ciągów znaków. W poniższym przykładzie pokazano *wewnętrzne przygotowanie ciągu* funkcji języka C#. Gdy program deklaruje co najmniej dwóch zmiennych identyczne ciągu, kompilator są przechowywane w tej samej lokalizacji. Przez wywołanie metody <xref:System.Object.ReferenceEquals%2A> metody, zobaczysz, że dwa ciągi faktycznie odnoszą się do tego samego obiektu w pamięci. Użyj <xref:System.String.Copy%2A?displayProperty=nameWithType> metody w celu uniknięcia wewnętrzne przygotowanie. Po dokonaniu kopii dwa ciągi mają lokalizacje innego magazynu, mimo że mają taką samą wartość. Uruchom poniższy przykład pokazanie ciągi `a` i `b` są *interned* oznacza mają tego samego magazynu. Ciągi `a` i `c` nie są.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Podczas testowania pod kątem równości ciągów, należy użyć metody, które jawnie określić, jakiego rodzaju porównania, których zamierzasz wykonać. Kod jest znacznie łatwiejsze w obsłudze i do odczytu. Użyj przeciążeń metody <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klasy, które trwają <xref:System.StringComparison> parametr wyliczenia. Należy określić typ porównania do wykonania. Unikaj używania `==` i `!=` operatorów podczas testowania pod kątem równości. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metod wystąpienia zawsze wykonuj porównania porządkowego uwzględniana wielkość liter. Są one głównie odpowiednie porządkowania ciągów w kolejności alfabetycznej.

Można intern ciąg lub pobrania odwołania do istniejącego ciągu interned przez wywołanie metody <xref:System.String.Intern%2A?displayProperty=nameWithType> metody. Aby ustalić, czy ciąg jest interned, należy wywołać <xref:System.String.IsInterned%2A?displayProperty=nameWithType> metody.

## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Ciągi](../programming-guide/strings/index.md)
- [Porównywanie ciągów](../../standard/base-types/comparing.md)
- [Globalizowanie i lokalizowanie aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)
