---
title: Funkcje ciągów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 645d19219481d22ade90f44aaecb62471eb915d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817206"
---
# <a name="string-functions-visual-basic"></a>Funkcje ciągów (Visual Basic)
W poniższej tabeli wymieniono funkcje, które zapewnia Visual Basic możliwość wyszukiwania ciągów i manipulowania nimi.  
  
|Metoda .NET framework|Opis|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Zwraca `Integer` reprezentującą kod znaku odpowiadający znakowi.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Zwraca znak skojarzony z określonym kodem znaku.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Zwraca tablicę wartości nieujemnych zawierającą podzbiór `String` tablica opartym na określonych kryteriach filtru.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Zwraca ciąg sformatowany zgodnie z instrukcjami zawartymi w formacie `String` wyrażenia.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Zwraca wyrażenie sformatowane jako wartość walutowa używająca symbolu waluty zdefiniowanego w Panelu sterowania systemu.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Zwraca wyrażenie ciągu reprezentujące wartość daty/godziny.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Zwraca wyrażenie sformatowane do postaci liczby.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Zwraca wyrażenie sformatowane jako wartość procentowa (tzn. pomnożona przez 100) ze znakiem % na końcu.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Zwraca liczbę całkowitą określającą początkowe położenie pierwszego wystąpienia jednego ciągu w innym.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Zwraca pozycję pierwszego wystąpienia jednego ciągu w innym, licząc od prawej strony ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Zwraca ciąg powstały z połączenia kilku podciągów zawartych w tablicy.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Zwraca ciąg lub znak przekonwertowany na małe litery.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Zwraca ciąg zawierający określoną liczbę znaków z lewej strony ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Zwraca liczbę całkowitą, która zawiera liczbę znaków w ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Zwraca ciąg wyrównany do lewej zawierający podany ciąg skorygowany do zadanej długości.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Zwraca ciąg zawierającą kopię określonego ciągu bez spacji wiodących.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Zwraca ciąg zawierający określoną liczbę znaków z ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Zwraca wartość typu ciąg, w którym określony podciąg został zastąpiony innym podciągiem określoną liczbę razy.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Zwraca ciąg zawierający określoną liczbę znaków z prawej strony ciągu.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Zwraca ciąg wyrównany do prawej zawierający podany ciąg skorygowany do zadanej długości.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Zwraca ciąg zawierającą kopię określonego ciągu bez spacji.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Zwraca ciąg składający się z określonej liczby spacji.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Zwraca nieujemną jednowymiarową tablicę zawierającą określoną liczbę podciągów.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Zwraca wartość -1, 0 lub 1, w oparciu o wyniki porównania ciągów.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Zwraca ciąg przekonwertowany WE wskazany.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Zwraca ciąg lub obiekt składający się z określonego znaku powtórzone określoną liczbę razy.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Zwraca ciąg, w którym kolejność znaków określonego ciągu została odwrócona.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Zwraca ciąg zawierającą kopię określonego ciągu bez spacji wiodących i końcowych.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Zwraca ciąg lub znak zawierający określony ciąg przekonwertowany na wielkie litery.|  
  
 Możesz użyć [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) instrukcję, aby określić, czy ciągi są porównywane, przy użyciu tekstu bez uwzględniania wielkości liter sortowania kolejności określane przez ustawienia regionalne systemu (`Text`) lub przez wewnętrzne binarne reprezentacje znaków () `Binary`). Domyślna metoda porównania tekstu jest `Binary`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `UCase` funkcja zwraca wersję z wielkimi literami ciągu.  
  
 [!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `LTrim` funkcję, aby odjąć wiodące spacje oraz `RTrim` funkcji końcowe spacje od zmiennej ciągu. Używa ona `Trim` funkcję, aby rozłożyć oba rodzaje miejsca do magazynowania.  
  
 [!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Mid` funkcja zwraca określoną liczbę znaków z ciągu.  
  
 [!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Len` aby wrócić liczbę znaków w ciągu.  
  
 [!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `InStr` funkcję, aby wrócić położenie pierwszego wystąpienia jednego ciągu w innym.  
  
 [!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje różne przypadki użycia `Format` funkcji do formatowania wartości przy użyciu zarówno `String` formatów i formatów zdefiniowanych przez użytkownika. Dla separatora daty (`/`), separatora godziny (`:`) oraz wskaźników AM/PM (`t` i `tt`), rzeczywiste formatowanie wyniku wyświetlanego w systemie zależy od ustawień regionalnych w kodzie. Gdy godziny i daty są wyświetlane w środowisku programistycznym, krótki format czasu i krótki format daty kodu są używane.  
  
> [!NOTE]
>  Dla ustawień regionalnych, które używają zegara 24-godzinnego, wskaźniki AM/PM (`t` i `tt`) nie będą niczego wyświetlać.  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Elementy członkowskie biblioteki środowiska uruchomieniowego Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)
- [Manipulowanie ciągami — podsumowanie](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
