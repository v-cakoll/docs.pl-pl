---
title: Wpływ kultury na ciągi
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 2520a7684b8710abd949543e3f17f77d3c631d22
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352475"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Wpływ kultury na ciągi w Visual Basic
Ta strona pomocy omawia sposób, w jaki Visual Basic używa informacji o kulturze do wykonywania konwersji ciągów i porównań.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kiedy używać ciągów specyficznych dla kultury  
 Zazwyczaj należy używać ciągów specyficznych dla kultury dla wszystkich danych prezentowanych i odczytywanych przez użytkowników, a w przypadku wewnętrznych danych aplikacji używać ciągów niezmiennych kultury.  
  
 Na przykład jeśli aplikacja prosi użytkowników o wprowadzenie daty jako ciągu, powinien oczekiwać, że użytkownicy sformatują ciągi zgodnie z ich kulturą, a aplikacja powinna odpowiednio przekonwertować ciąg. Jeśli aplikacja wyświetli tę datę w interfejsie użytkownika, powinna zaprezentować ją w kulturze użytkownika.  
  
 Jeśli jednak aplikacja przekaże datę do serwera centralnego, powinien sformatować ciąg zgodnie z jedną określoną kulturą, aby uniknąć pomyłek między potencjalnie różnymi formatami daty.  
  
## <a name="culture-sensitive-functions"></a>Funkcje zależne od kultury  
 Wszystkie Visual Basic funkcje konwersji ciągów (z wyjątkiem funkcji `Str` i `Val`) używają informacji o kulturze aplikacji w celu upewnienia się, że konwersje i porównania są odpowiednie dla kultury użytkownika aplikacji.  
  
 Klucz, aby pomyślnie korzystać z funkcji konwersji ciągów w aplikacjach uruchamianych na komputerach z różnymi ustawieniami kultury, ma zrozumieć, które funkcje używają określonego ustawienia kultury, i które używają bieżącego ustawienia kultury. Zauważ, że ustawienia kultury aplikacji są domyślnie dziedziczone z ustawień kultury systemu operacyjnego. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>i [typów funkcji konwersji](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (konwertuje liczby do ciągów) i `Val` (konwertuje ciągi na liczby) funkcje nie używają informacji o kulturze aplikacji podczas konwersji między ciągami i liczbami. Zamiast tego rozpoznaje tylko kropkę (.) jako prawidłowy separator dziesiętny. Podobne w kulturze analogowe funkcje te są następujące:  
  
- **Konwersje wykorzystujące bieżącą kulturę.** Funkcje `CStr` i `Format` konwertują liczbę na ciąg, a funkcje `CDbl` i `CInt` konwertują ciąg na liczbę.  
  
- **Konwersje wykorzystujące określoną kulturę.** Każdy obiekt liczb ma metodę `ToString(IFormatProvider)`, która konwertuje liczbę na ciąg i metodę `Parse(String, IFormatProvider)`, która konwertuje ciąg na liczbę. Na przykład typ `Double` zapewnia metody <xref:System.Double.ToString%28System.IFormatProvider%29> i <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>.  
  
 Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Conversion.Str%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Korzystanie z określonej kultury  
 Załóżmy, że tworzysz aplikację wysyłającą datę (sformatowaną jako ciąg) do usługi sieci Web. W takim przypadku aplikacja musi używać określonej kultury do konwersji ciągów. Aby zilustrować przyczynę, należy wziąć pod uwagę wynik korzystania z metody <xref:System.DateTime.ToString>ej daty: Jeśli aplikacja używa tej metody do formatowania daty 4 lipca 2005, zwraca "7/4/2005 12:00:00 AM" podczas uruchamiania z kulturą Stany Zjednoczone angielski (EN-US), ale zwraca "04.07.2005 00:00:00", gdy jest uruchamiany z niemieckim (de-DE) kulturą.  
  
 Gdy konieczne jest przeprowadzenie konwersji ciągów w określonym formacie kultury, należy użyć klasy `CultureInfo`, która jest wbudowana w .NET Framework. Można utworzyć nowy obiekt `CultureInfo` dla określonej kultury, przekazując nazwę kultury do konstruktora <xref:System.Globalization.CultureInfo.%23ctor%2A>. Obsługiwane nazwy kultur są wymienione na stronie pomocy klasy <xref:System.Globalization.CultureInfo>.  
  
 Alternatywnie można uzyskać wystąpienie *niezmiennej kultury* z właściwości <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kultura niezmienna jest oparta na kulturze angielskiej, ale istnieją pewne różnice. Na przykład Niezmienna kultura określa 24-godzinny zegar zamiast 12-godzinnego zegara.  
  
 Aby przekonwertować datę na ciąg kultury, przekaż obiekt <xref:System.Globalization.CultureInfo> do metody <xref:System.DateTime.ToString%28System.IFormatProvider%29> obiektu Date. Na przykład poniższy kod wyświetla "07/04/2005 00:00:00", niezależnie od ustawień kultury aplikacji.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> Literały daty są zawsze interpretowane zgodnie z kulturą w języku angielskim.  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Istnieją dwie ważne sytuacje, w których są potrzebne porównania ciągów:  
  
- **Sortowanie danych do wyświetlania użytkownikowi.** Użyj operacji opartych na bieżącej kulturze, aby ciągi były odpowiednio sortowane.  
  
- **Ustalanie, czy dwa ciągi wewnętrzne aplikacji dokładnie pasują (zazwyczaj ze względów bezpieczeństwa).** Użyj operacji, które zignorują bieżącą kulturę.  
  
 Oba typy porównań można wykonać za pomocą funkcji <xref:Microsoft.VisualBasic.Strings.StrComp%2A> Visual Basic. Określ opcjonalny argument `Compare`, aby kontrolować typ porównania: `Text` dla większości `Binary` wejściowych i wyjściowych, aby określić dokładne dopasowania.  
  
 Funkcja `StrComp` zwraca liczbę całkowitą, która wskazuje relację między dwoma porównanymi ciągami na podstawie kolejności sortowania. Wartość dodatnia wyniku wskazuje, że pierwszy ciąg jest większy niż drugi ciąg. Wynik ujemny wskazuje, że pierwszy ciąg jest mniejszy, a zero oznacza równość między ciągami.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Można również użyć .NET Framework partnera funkcji `StrComp`, metody <xref:System.String.Compare%2A?displayProperty=nameWithType>. Jest to statyczna, przeciążona metoda klasy ciągów podstawowych. Poniższy przykład ilustruje sposób użycia tej metody:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 Aby uzyskać dokładniejszą kontrolę nad sposobem wykonywania porównań, można użyć dodatkowych przeciążeń metody <xref:System.String.Compare%2A>. Za pomocą metody <xref:System.String.Compare%2A?displayProperty=nameWithType> można użyć argumentu `comparisonType`, aby określić, który typ porównania ma być używany.  
  
|Wartość argumentu `comparisonType`|Typ porównania|Kiedy stosować|  
|---|---|---|  
|`Ordinal`|Porównanie oparte na bajtach składników ciągu ".|Użyj tej wartości podczas porównywania: identyfikatory z uwzględnieniem wielkości liter, ustawienia związane z zabezpieczeniami lub inne identyfikatory inne niż językowe, w których bajty muszą być dokładnie zgodne.|  
|`OrdinalIgnoreCase`|Porównanie oparte na bajtach składników ciągu ".<br /><br /> `OrdinalIgnoreCase` używa informacji o kulturze niezmiennej, aby określić, kiedy dwa znaki różnią się tylko wielkością liter.|Użyj tej wartości podczas porównywania: identyfikatorów bez uwzględniania wielkości liter, ustawień związanych z zabezpieczeniami i danych przechowywanych w systemie Windows.|  
|`CurrentCulture` lub `CurrentCultureIgnoreCase`|Porównanie w oparciu o interpretację ciągów w bieżącej kulturze.|Użyj tych wartości podczas porównywania: dane, które są wyświetlane dla użytkownika, większość danych wejściowych użytkownika i inne dane, które wymagają interpretacji językowej.|  
|`InvariantCulture` lub `InvariantCultureIgnoreCase`|Porównanie w oparciu o interpretację ciągów w niezmiennej kulturze.<br /><br /> Jest to inne niż `Ordinal` i `OrdinalIgnoreCase`, ponieważ kultura niezmienna traktuje znaki poza zaakceptowanym zakresem jako równoważne znaki niezmienne.|Te wartości są używane tylko w przypadku porównywania utrwalania danych lub wyświetlania ważnych danych, które wymagają ustalonej kolejności sortowania.|  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli aplikacja podejmuje decyzje dotyczące zabezpieczeń na podstawie wyniku porównania lub operacji zmiany wielkości liter, operacja powinna używać metody <xref:System.String.Compare%2A?displayProperty=nameWithType> i przekazywać `Ordinal` lub `OrdinalIgnoreCase` dla argumentu `comparisonType`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo>
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
