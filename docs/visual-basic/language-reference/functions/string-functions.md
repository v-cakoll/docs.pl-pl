---
title: Funkcje ciągów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: f6c7f28cee03c2d5ac258cf1e2c8956225334f7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604149"
---
# <a name="string-functions-visual-basic"></a>Funkcje ciągów (Visual Basic)
W poniższej tabeli wymieniono funkcje, które zapewnia Visual Basic do wyszukiwania i manipulowania ciągami.  
  
|.NET framework — metoda|Opis|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Zwraca `Integer` wartość reprezentującą kod znaku odpowiadający znakowi.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Zwraca znak skojarzony z podanym kodem znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Zwraca tablicę wartości nieujemnych zawierającą podzbiór `String` tablicy oparciu o określone kryteria filtru.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Zwraca ciąg sformatowany zgodnie z instrukcjami zawartymi w formacie `String` wyrażenia.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Zwraca wyrażenie sformatowane jako wartość walutowa używająca symbolu waluty zdefiniowanego w Panelu sterowania systemu.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Zwraca ciąg reprezentujący wartość daty/godziny.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Zwraca wyrażenie sformatowane jako liczby.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Zwraca wyrażenie sformatowane jako wartość procentowa (tzn. pomnożona przez 100) znakiem %.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Zwraca liczbę całkowitą określającą początkowe położenie pierwszego wystąpienia jednego ciągu w innym.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Zwraca pozycję pierwszego wystąpienia jednego ciągu w innym, licząc od prawego końca ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Zwraca ciąg powstały z połączenia kilku podciągów zawartych w tablicy.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Zwraca ciąg lub znak przekonwertowany na małe litery.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Zwraca ciąg zawierający określoną liczbę znaków od lewego końca ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Zwraca liczbę całkowitą, która zawiera liczbę znaków w ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Zwraca ciąg wyrównany do lewej zawierający podany ciąg skorygowany do zadanej długości.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Zwraca ciąg zawierający kopię podanego ciągu bez spacji początkowych.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Zwraca ciąg zawierający określoną liczbę znaków z ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Zwraca wartość typu ciąg, w której określony podciąg został zamieniony na inny podciąg określoną liczbę razy.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Zwraca ciąg zawierający określoną liczbę znaków od prawego końca ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Zwraca ciąg wyrównany do prawej zawierający podany ciąg skorygowany do zadanej długości.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Zwraca ciąg zawierający kopię podanego ciągu bez nie spacje końcowe.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Zwraca ciąg zawierający podaną liczbę spacji.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Zwraca nieujemną jednowymiarową tablicę zawierającą podaną liczbę podciągów.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Zwraca wartość -1, 0 lub 1, na podstawie wyniku porównania ciągów.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Zwraca ciąg przekonwertowany WE wskazany.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Zwraca ciąg lub obiekt zawierający podany znak powtórzony określoną liczbę razy.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Zwraca wartość typu ciąg, w którym została odwrócona kolejność znaków określonego ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Zwraca ciąg zawierający kopię podanego ciągu bez spacji wiodących lub końcowych.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Zwraca ciąg lub znak odpowiadający wybranemu ciągowi po konwersji na wielkie litery.|  
  
 Można użyć [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) instrukcji, aby określić, czy ciągi są porównywane przy użyciu bez uwzględniania wielkości liter tekstu sortowania kolejności ustalonej w ustawieniach regionalnych systemu (`Text`) lub wewnętrzny reprezentacje binarne (znaków `Binary`). Domyślną metodę porównywania tekst jest `Binary`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `UCase` funkcja zwracająca wielkie wersji ciągu.  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `LTrim` funkcji spacje początkowe i `RTrim` funkcji końcowe spacje ze zmienną typu string. Używa `Trim` funkcji obu typów spacji.  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Mid` funkcja zwraca określoną liczbę znaków z ciągu.  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Len` do zwrócenia liczbę znaków w ciągu.  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `InStr` funkcja zwraca pozycję pierwszego wystąpienia jednego ciągu w innym.  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano różnych zastosowań `Format` funkcji, aby obie wartości formatu `String` formaty i formaty zdefiniowane przez użytkownika. Separatora daty (`/`), czas separatora (`:`) oraz wskaźniki AM/PM (`t` i `tt`), rzeczywiste sformatowane wyniki wyświetlane w systemie zależy od ustawień regionalnych jest przy użyciu kodu. Gdy godziny i daty są wyświetlane w środowisku programistycznym, format godziny krótkiej i format daty krótkiej kod ustawień regionalnych są używane.  
  
> [!NOTE]
>  Dla ustawień regionalnych, korzystających z 24-godzinnym, wskaźniki AM/PM (`t` i `tt`) wyświetlić pustą.  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Elementy członkowskie biblioteki środowiska uruchomieniowego Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)  
 [Manipulowanie ciągami — podsumowanie](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
