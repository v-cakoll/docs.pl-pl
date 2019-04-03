---
title: Wpływ kultury na ciągi w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834624"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Wpływ kultury na ciągi w Visual Basic
Tej strony Pomocy opisano, jak Visual Basic używa informacji o kulturze przeprowadzenie ciąg konwersje i porównań.  
  
## <a name="when-to-use-culture-specific-strings"></a>Kiedy należy używać ciągów specyficzne dla kultury  
 Zazwyczaj należy używać ciągów specyficzne dla kultury dla wszystkich danych przedstawiony w usłudze i odczytu z użytkowników i używać parametrów niezmiennej kultury dla danych wewnętrznych aplikacji.  
  
 Na przykład jeśli aplikacja prosi użytkowników podania datę jako ciąg znaków, należy się spodziewać użytkownicy do formatowania ciągów zgodnie z ich kultury i aplikacji należy przekonwertować ciąg odpowiednio. Jeśli następnie aplikacja wyświetla datę w interfejsie użytkownika, ona powinny prezentować kultury użytkownika.  
  
 Jednak jeśli aplikacja przekazuje daty do centralnego serwera, należy sformatować ciąg według jedną określoną kulturę, aby zapobiec niejasności między formatami potencjalnie inną datę.  
  
## <a name="culture-sensitive-functions"></a>Funkcje zależne od kultury  
 Wszystkie funkcje konwersji ciągów w Visual Basic (z wyjątkiem `Str` i `Val` funkcji) Użyj informacji o kulturze aplikacji, aby upewnić się, konwersji i porównania są właściwe dla kultury aplikacji użytkownik.  
  
 Kluczem do pomyślnie przy użyciu funkcji konwersji ciągów w aplikacjach, które są uruchamiane na komputerach z ustawieniami inną kulturę jest zrozumienie, jakie funkcje ustawienie określonej kultury, a które użyć bieżącego ustawienia kultury. Należy zauważyć, że ustawienia kultury aplikacji domyślnie odziedziczone ustawienia kultury systemu operacyjnego. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, i [funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 `Str` (Konwertuje liczb na ciągi znaków) i `Val` funkcji (konwertuje ciągi na liczby) należy używać informacji o kulturze aplikacji podczas konwersji między ciągi i liczby. Zamiast tego mogą rozpoznać tylko kropki (.) jako separator dziesiętny prawidłowy. Kulturalnie obsługujących podobne produkty z tych funkcji są następujące:  
  
-   **Konwersje, które używają bieżącej kultury.** `CStr` i `Format` funkcji konwertuje liczbę na ciąg i `CDbl` i `CInt` funkcji konwertuje ciąg na liczbę.  
  
-   **Konwersje, które używają określonej kultury.** Każdy obiekt numer ma `ToString(IFormatProvider)` metodę, która konwertuje liczbę na ciąg i `Parse(String, IFormatProvider)` metodę, która konwertuje ciąg na liczbę. Na przykład `Double` typ zapewnia <xref:System.Double.ToString%28System.IFormatProvider%29> i <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> metody.  
  
 Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Conversion.Str%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>Przy użyciu określonej kultury  
 Wyobraź sobie, że opracowujesz aplikację, która wysyła daty (sformatowany jako ciąg) do usługi sieci Web. W tym przypadku aplikacja musi używać określonej kultury do konwersji ciągu. W celu zilustrowania Dlaczego, należy wziąć pod uwagę wynik za pomocą daty <xref:System.DateTime.ToString> metody: Jeśli aplikacja używa tej metody do formatowania daty 4 lipca 2005, zwraca "7/4/2005 12:00:00 AM" uruchamiania z kulturą Stanów Zjednoczonych angielski (en US), ale zwraca "04.07.2005 00:00:00" uruchamiania z kulturą niemiecki (de-DE).  
  
 Gdy zachodzi potrzeba wykonania konwersji ciągu w formacie określonej kultury, należy użyć `CultureInfo` klasy, która jest wbudowana w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Można utworzyć nową `CultureInfo` obiektu dla określonej kultury, przekazując nazwę kultury, aby <xref:System.Globalization.CultureInfo.%23ctor%2A> konstruktora. Nazwy kultury obsługiwane są wymienione w <xref:System.Globalization.CultureInfo> klasy strony pomocy.  
  
 Alternatywnie można pobrać wystąpienia *niezmiennej kultury* z <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> właściwości. Zależy od kultury niezmiennej kultury angielski, ale istnieją pewne różnice. Na przykład niezmiennej kultury określa zegara 24-godzinnego, zamiast 12-godzinnym.  
  
 Aby przekonwertować datę na ciąg kultury, należy przekazać <xref:System.Globalization.CultureInfo> obiektu do obiektu daty <xref:System.DateTime.ToString%28System.IFormatProvider%29> metody. Na przykład, poniższy kod wyświetla "07/04/2005 00:00:00", niezależnie od ustawień kultury aplikacji.  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Literały daty są zawsze interpretowane zgodnie z kulturą angielskiego.  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Istnieją dwie ważne sytuacje, w których porównania ciągów są wymagane:  
  
-   **Sortowanie danych w celu wyświetlenia użytkownikowi.** Użyj operacji opartych na bieżącej kultury, aby posortować ciągi, odpowiednio.  
  
-   **Określanie, jeśli dwa ciągi wewnętrznych aplikacji dokładnie odpowiadać (zwykle ze względów bezpieczeństwa).** Użyj operacji, które nie brać pod uwagę bieżącej kultury.  
  
 Można wykonać obu rodzajów porównań, za pomocą Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A> funkcji. Określ opcjonalne `Compare` argumentem do sterowania typ porównania: `Text` dla większości danych wejściowych i wyjściowych `Binary` określania dokładne dopasowania.  
  
 `StrComp` Funkcji zwraca liczbę całkowitą, wskazującą, związek między dwa ciągi w porównaniu na podstawie kolejności sortowania. Wartość dodatnia wynik wskazuje, czy pierwszy ciąg jest większy niż drugi ciąg. Wynik ujemny wskazuje pierwszy ciąg jest mniejszy, wartość zero wskazuje równości pomiędzy ciągi.  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 Można również użyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] partner `StrComp` funkcji <xref:System.String.Compare%2A?displayProperty=nameWithType> metody. Jest to statyczne, przeciążone metody klasy bazowej ciągu. W poniższym przykładzie pokazano, jak ta metoda jest używana:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 W przypadku bardziej precyzyjną kontrolę nad jak porównania są wykonywane, można użyć dodatkowych przeciążenia <xref:System.String.Compare%2A> metody. Za pomocą <xref:System.String.Compare%2A?displayProperty=nameWithType> metody, można użyć `comparisonType` argumentu, aby określić typ porównania do użycia.  
  
|Wartość `comparisonType` argumentu|Typ porównania|Kiedy stosować|  
|---|---|---|  
|`Ordinal`|Porównanie, w bajtach składników ciągów.|Użyj tej wartości podczas porównywania: identyfikatory uwzględniana wielkość liter, ustawienia związane z zabezpieczeniami lub innych nielingwistyczne identyfikatorów, w którym bajtów musi dokładnie pasować.|  
|`OrdinalIgnoreCase`|Porównanie, w bajtach składników ciągów.<br /><br /> `OrdinalIgnoreCase` informacje Niezmienna kultura są używane do określania, kiedy dwa znaki różnią się jedynie wielkość liter.|Użyj tej wartości podczas porównywania: bez uwzględniania wielkości liter identyfikatorów, ustawienia związane z zabezpieczeniami i dane przechowywane w Windows.|  
|`CurrentCulture` lub `CurrentCultureIgnoreCase`|Porównań opartych na interpretację ciągów w bieżącej kultury.|Podczas porównywania, używając następujących wartości: danych, który jest wyświetlany użytkownikowi, większość danych wejściowych użytkownika i innych danych, które wymagają interpretacji językowej.|  
|`InvariantCulture` lub `InvariantCultureIgnoreCase`|Porównań opartych na interpretację ciągów niezmiennej kultury.<br /><br /> Stanowi to odmianę `Ordinal` i `OrdinalIgnoreCase`, ponieważ niezmiennej kultury traktuje znaki spoza zakresu akceptowanych jako równoważne znaki niezmienna.|Tylko podczas porównywania utrwalanie danych lub wyświetlania językowo odpowiednie dane, które wymaga stałej sortowania, należy użyć tych wartości.|  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli aplikacja podejmuje decyzje dotyczące bezpieczeństwa, w oparciu o wyniki porównania lub operację zmiany sprawy, a następnie operacja powinna użyć <xref:System.String.Compare%2A?displayProperty=nameWithType> metody i przekazać `Ordinal` lub `OrdinalIgnoreCase` dla `comparisonType` argumentu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo>
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
