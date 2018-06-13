---
title: 'Porady: porównywanie ciągów — przewodnik C#'
description: Dowiedz się, jak porównać i kolejność wartości ciągu, z lub bez przypadku z lub bez kolejności określonej kultury
ms.date: 03/20/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: e9f4216af6073a352bef1efb59eea0ddeda5fc4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218111"
---
# <a name="how-to-compare-strings-in-c"></a>Sposób porównywania ciągów w języku C# #

Porównywanie ciągów do odpowiedzi, jednego z dwóch pytań: "Są te dwa ciągi równe?" lub "W jakiej kolejności należy te ciągi umieścić podczas sortowania?"

Te dwa pytania są skomplikowany czynników mających wpływ na porównania ciągu: 
- Można wybrać porównanie liczby porządkowej lub językową.
- Można wybrać, jeśli przypadek ma znaczenie.
- Możesz wybrać kultury porównań określonych.
- Comparisions językowe są kultury i platformy zależnej.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Podczas porównywania ciągów, należy zdefiniować kolejności między nimi. Porównania są używane do sortowania sekwencję ciągów. Po sekwencja w kolejności znane łatwiej wyszukiwanie, zarówno w przypadku oprogramowania i dla ludzi. Pozostałych porównań może sprawdzić, czy ciągi są takie same. Te sprawdzenia symetryczność są podobne do równości, ale niektóre różnice, takie jak różnice wielkości liter, można zignorować.

## <a name="default-ordinal-comparisons"></a>Domyślny numer porządkowy porównania

Najbardziej typowe operacje <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i <xref:System.String.Equals%2A?displayProperty=nameWithType> lub <xref:System.String.op_Equality%2A?displayProperty=nameWithType> używa porządkowej porównania porównania z uwzględnieniem wielkości liter i bieżącej kultury. W poniższym przykładzie przedstawiono wyniki.

[!code-csharp-interactive[Comparing strings using an ordinal comparison](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#1)]

{Numer porządkowy porównania nie uwzględniać językowe reguł podczas porównywania ciągów. Będą one porównywanie ciągów znaków po znaku. Porównania z uwzględnieniem wielkości liter w ich porównania używać wielkich liter. Najważniejsze punkt o tych metodach porównania domyślne jest, że używają one bieżącej kultury, wyniki zależą od ustawień regionalnych i językowych ustawień maszyny przepływają. Są to porównania nie nadaje się do porównania gdzie kolejności powinny być zgodne w maszyny lub lokalizacji.

## <a name="case-insensitive-ordinal-comparisons"></a>Porównywanie porządkowych bez uwzględniania wielkości liter

<xref:System.String.Equals%2A?displayProperty=nameWithType> Metody umożliwia określenie <xref:System.StringComparison> wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> do określenia porównania bez uwzględniania wielkości liter. Istnieje również statycznego <xref:System.String.Compare%2A> metodę, która zawiera logiczną argumentu, aby określić porównania bez uwzględniania wielkości liter. Zostały one przedstawione w poniższym kodzie:

[!code-csharp-interactive[Comparing strings ignoring case](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#2)]

## <a name="linguistic-comparisons"></a>Porównywanie językowe

Ciągi również może zostać określona przy użyciu języka reguł dla bieżącej kultury.
To jest czasami nazywany "word porządek sortowania". Podczas wykonywania językowe porównanie, niektóre innych niż alfanumeryczne znaki Unicode może być specjalne wagi przypisane. Na przykład łącznik "-" może być bardzo małych wagi przypisane do niego "zawiera" oraz "coop" będą wyświetlane obok siebie w kolejności sortowania. Ponadto niektóre znaki Unicode może być taka sama sekwencję characterss alfanumeryczne. W poniższym przykładzie użyto frazę "One taniec na ulicy." w języku niemieckim "ss" i "ß". Zależnej (w systemie Windows), "port" jest równa Essetz niemiecki: znak "ß" zarówno "en US" i "de-DE" kultur. 

[!code-csharp-interactive[Comparing strings using linguistic rules](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#3)]

W przykładzie pokazano zależnego systemu operacyjnego rodzaj językowe porównania. Host interaktywny okna jest hoście z systemem Linux. Porównania językowe i liczby porządkowej działają tak samo. Jeśli ten sam przykład uruchomienia na hoście systemu Windows, zobaczysz następujące dane wyjściowe:

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

W systemie Windows, kolejność sortowania "Kopiuj", "coop" i "zawiera" zmian po zmianie językowe porównanie liczby porządkowej porównania. Dwa zdania niemieckim także porównać inaczej przy użyciu porównanie różnych typów.

## <a name="comparisons-using-specific-cultures"></a>Porównywanie za pomocą określonej kultury

W tym przykładzie przechowuje <xref:System.Globalization.CultureInfo> dla bieżącej kultury.
Oryginalny kultury można ustawić i pobrać dla bieżącego obiektu wątku. Porównanie są wykonywane przy użyciu <xref:System.StringComparison.CurrentCulture> wartość, aby zapewnić porównanie specyficzne dla kultury.

Kultura używana dotyczy językowe porównania. W poniższym przykładzie przedstawiono porównanie dwa zdania niemieckim przy użyciu kultury "en US" i "de-DE" kultury wyników:

[!code-csharp-interactive[Comparing strings across cultures](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#4)]

Zależne od kultury porównań są zwykle używane porównywanie i sortowanie ciągów wprowadzania przez użytkowników z innych ciągów wejściowych przez użytkowników. Znaki i konwencje sortowania tych ciągów mogą się różnić w zależności od ustawień regionalnych komputera użytkownika. Nawet ciągów, które zawierają znaki identyczne może sortować inaczej w zależności od kultury bieżącej wątku. Ponadto, spróbuj ten przykładowy kod lokalnie na komputerze z systemem Windows i będą następujące wyniki:

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Comparisions językowe są zależne od bieżącej kultury i są zależne systemu operacyjnego. Użytkownik musi uwzględniać który podczas pracy z porównywania ciągów.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Sortowanie i wyszukiwanie ciągów w tablice

Poniższe przykłady przedstawiają sposób sortowanie i wyszukiwanie ciągów w tablicy przy użyciu językowe porównanie zależne od bieżącej kultury. Użyj statycznych <xref:System.Array> metod, które przyjmują <xref:System.StringComparer?displayProperty=nameWithType> parametru.

W tym przykładzie przedstawiono sposób sortowania na tablicę ciągów za pomocą bieżącej kultury: 

[!code-csharp-interactive[Sorting an array of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#5)]

Gdy tablica jest sortowana, możesz wyszukać wpisów przy użyciu wyszukiwanie binarne. Wyszukiwanie binarne rozpoczyna się w środku kolekcji, aby ustalić którym połowa kolekcji może zawierać ciągu używanych. Każde kolejne porównanie dzieli pozostała część kolekcji o połowę.  Tablica jest posortowana przy użyciu <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. Funkcja lokalna `ShowWhere` Wyświetla informacje o którym znaleziono ciąg. Jeśli nie można odnaleźć ciągu, zwrócona wartość wskazuje, gdzie będzie Jeśli go znaleziono.

[!code-csharp-interactive[Searching in a sorted array](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#6)]

## <a name="ordinal-sorting-and-searching-in-collections"></a>{Numer porządkowy sortowanie i wyszukiwanie w kolekcjach

Poniższy kod używa <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> klasy kolekcji do przechowywania ciągów. Ciągi są sortowane przy użyciu <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metody. Ta metoda wymaga delegata, który porównuje i porządkuje dwóch ciągów. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Metoda zawiera porównanie funkcji. Uruchom próbkę i obserwować kolejności. Ta operacja sortowania używa porządkową sortowania z uwzględnieniem wielkości liter. Należy użyć statycznych <xref:System.String.Compare%2A?displayProperty=nameWithType> metody do określania reguł różnych porównania.

[!code-csharp-interactive[Sorting a list of strings](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#7)]

Po sortować listy ciągów mogą być wyszukiwane przy użyciu wyszukiwanie binarne. Poniższy przykład pokazuje, jak w sortowanych na liście, używając tej samej funkcji porównania. Funkcja lokalna `ShowWhere` pokazuje, gdzie lub byłoby używanych tekstu:

[!code-csharp-interactive[csProgGuideStrings#11](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#8)]

Zawsze należy używać tego samego typu porównania sortowanie i wyszukiwanie. Sortowanie i wyszukiwanie daje nieprzewidziane wyniki przy użyciu porównanie różnych typów. 

Kolekcja klas takich jak <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>, i <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ma konstruktorów przyjmujących <xref:System.StringComparer?displayProperty=nameWithType> parametru, gdy typ elementów lub kluczy to `string`. Ogólnie rzecz biorąc, należy te konstruktorów w miarę możliwości używać i określ <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Równość odwołania i interning ciągu

Brak próbek używanych <xref:System.Object.ReferenceEquals%2A>. Ta metoda określa, czy dwa ciągi są tego samego obiektu. Może to prowadzić do niespójnych wyników w porównywania ciągów. W poniższym przykładzie pokazano *interning ciąg* funkcji języka C#. Jeśli program deklaruje co najmniej dwa identyczne ciągu zmiennych, kompilator przechowuje je w tej samej lokalizacji. Wywołując <xref:System.Object.ReferenceEquals%2A> metody widać, że dwa ciągi faktycznie odwołują się do tego samego obiektu w pamięci. Użyj <xref:System.String.Copy%2A?displayProperty=nameWithType> metody w celu uniknięcia interning. Po dokonaniu kopii dwa ciągi ma inną lokalizację, mimo że mają one taką samą wartość. Uruchom poniższy przykład pokazanie ciągi `a` i `b` są *interned* oznacza mają ten sam obiekt magazynu. Ciągi `a` i `c` nie są.

[!code-csharp-interactive[Demonstrating string interning](../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs#9)]

> [!NOTE]
> Podczas testowania pod kątem równości ciągów, należy użyć metody, które jawnie określić, jakiego rodzaju porównania zamierzasz wykonać. Kod jest bardziej łatwy w obsłudze i do odczytu. Użyj przeciążeń metody <xref:System.String?displayProperty=nameWithType> i <xref:System.Array?displayProperty=nameWithType> klas, które trwają <xref:System.StringComparison> parametru wyliczenia. Należy określić typ porównania do wykonania. Unikaj używania `==` i `!=` operatory podczas testowania pod kątem równości. <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Wystąpienia metody zawsze wykonują porządkowej porównania z uwzględnieniem wielkości liter. Są one przede wszystkim odpowiednie alfabetycznie porządkowania ciągów.

## <a name="see-also"></a>Zobacz także
 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>  
 <xref:System.StringComparer?displayProperty=nameWithType>  
 [Ciągi](../programming-guide/strings/index.md)  
 [Porównywanie ciągów](../../standard/base-types/comparing.md)  
 [Globalizowanie i lokalizowanie aplikacji](/visualstudio/ide/globalizing-and-localizing-applications)