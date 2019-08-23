---
title: Rozwiązywanie problemów związanych z typami danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933232"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Rozwiązywanie problemów związanych z typami danych (Visual Basic)
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas wykonywania operacji na wewnętrznych typach danych.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Wyrażenia zmiennoprzecinkowe nie są porównywane jako równe  
 Podczas pracy z liczbami zmiennoprzecinkowymi ([pojedynczym typem danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) i [podwójnym typem danych](../../../../visual-basic/language-reference/data-types/double-data-type.md)) należy pamiętać, że są one przechowywane jako ułamki binarne. Oznacza to, że nie mogą przechowywać dokładnej reprezentacji żadnej ilości, która nie jest częścią binarną (w postaci k/(2 ^ n), gdzie k i n są liczbami całkowitymi). Na przykład 0,5 (= 1/2) i 0,3125 (= 5/16) mogą być przechowywane jako dokładne wartości, natomiast 0,2 (= 1/5) i 0,3 (= 3/10) mogą być tylko przybliżami.  
  
 Z powodu tej niedokładności nie można polegać na dokładnych wynikach podczas wykonywania operacji na wartościach zmiennoprzecinkowych. W szczególności dwie wartości, które są teoretycznie równe, mogą mieć nieco inne reprezentacje.  
  
| Aby porównać ilości zmiennoprzecinkowe | 
|---| 
|1.  Oblicz wartość bezwzględną różnicy przy użyciu <xref:System.Math.Abs%2A> metody <xref:System.Math> klasy w <xref:System> przestrzeni nazw.<br />2.  Należy określić akceptowalną maksymalną różnicę, tak aby można było rozważyć, że te dwie ilości będą równe w praktyce, jeśli ich różnica nie jest większa.<br />3.  Porównaj wartość bezwzględną różnicy z akceptowalną różnicą.|  
  
 Poniższy przykład ilustruje nieprawidłowe i prawidłowe porównanie dwóch `Double` wartości.  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 W poprzednim przykładzie zastosowano <xref:System.Double.ToString%2A> metodę <xref:System.Double> struktury, aby można było `CStr` określić lepszą precyzję niż użycie słowa kluczowego. Wartość domyślna to 15 cyfr, ale format "G17" rozszerza go do 17 cyfr.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Operator mod nie zwraca dokładnego wyniku  
 Ze względu na niedokładność magazynu zmiennoprzecinkowego [operator mod](../../../../visual-basic/language-reference/operators/mod-operator.md) może zwrócić nieoczekiwany wynik, gdy co najmniej jeden operand jest zmiennoprzecinkowy.  
  
 [Typ danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie używa reprezentacji zmiennoprzecinkowej. Wiele liczb, które są `Single` dokładne i `Double` są dokładne `Decimal` (na przykład 0,2 i 0,3). Chociaż arytmetyka jest wolniejsza `Decimal` niż w liczbie zmiennoprzecinkowej, może być cenny spadek wydajności, aby osiągnąć lepszą precyzję.  
  
|Aby znaleźć liczbę całkowitą reszty liczb zmiennoprzecinkowych|  
|---|  
|1.  Zadeklaruj zmienne `Decimal`jako.<br />2.  Użyj znaku `D` typu literału `Decimal`, aby wymusić literały, na wypadek, gdyby ich wartości `Long` są za duże dla typu danych.|  
  
 Poniższy przykład ilustruje potencjalną niedokładność argumentów operacji zmiennoprzecinkowych.  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 W poprzednim przykładzie zastosowano <xref:System.Double.ToString%2A> metodę <xref:System.Double> struktury, aby można było `CStr` określić lepszą precyzję niż użycie słowa kluczowego. Wartość domyślna to 15 cyfr, ale format "G17" rozszerza go do 17 cyfr.  
  
 Ponieważ `zeroPointTwo` jest`Double`, jego wartość dla 0,2 to nieskończonie powtarzające się ułamek binarny z przechowywaną wartością 0.20000000000000001. Dzielenie 2,0 przez tę ilość daje 9.9999999999999995 z pozostałą częścią 0.19999999999999991.  
  
 W wyrażeniu dla `decimalRemainder`, znak `D` typu literału wymusza, aby oba operandy do, i 0,2 były `Decimal`precyzyjną reprezentacją. W związku `Mod` z tym operator zwraca oczekiwaną resztę z 0,0.  
  
 Należy pamiętać, że nie jest wystarczające do `decimalRemainder` deklarowania jako `Decimal`. Należy również `Decimal`wymusić, aby literały lub używać `Double` ich domyślnie, i `decimalRemainder` otrzymują tę samą niedokładną wartość `doubleRemainder`, co.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean nie jest dokładnie konwertowany na typ liczbowy  
 Wartości [typu danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) nie są przechowywane jako liczby, a przechowywane wartości nie są równoważne z liczbami. W celu zapewnienia zgodności z wcześniejszymi wersjami Visual Basic udostępnia słowa kluczowe konwersji `CBool`( `CInt`[Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md),,, itd.) `Boolean` w celu konwersji między typami i. Jednak inne języki czasami wykonują te konwersje inaczej, tak jak metody .NET Framework.  
  
 Nigdy nie należy pisać kodu, który opiera się na równoważnych wartościach `False`liczbowych dla `True` i. Zawsze, gdy jest to możliwe, należy `Boolean` ograniczyć użycie zmiennych do wartości logicznych, dla których zostały zaprojektowane. Jeśli trzeba mieszać `Boolean` i liczbować wartości, należy zapoznać się z wybraną metodą konwersji.  
  
### <a name="conversion-in-visual-basic"></a>Konwersja w Visual Basic  
 W `CType` przypadku użycia słowa kluczowego konwersji lub `Boolean` `CBool` do konwersji liczbowych typów danych na, `False` wartość 0 staje się i `True`wszystkie inne wartości staną się nieodpowiednie. Konwersja `Boolean` wartości na typy liczbowe przy użyciu `False` słów kluczowych konwersji zmieni się na 0 i `True` zmieni się-1.  
  
### <a name="conversion-in-the-framework"></a>Konwersja w strukturze  
 <xref:System.Convert.ToInt32%2A> Metoda klasy<xref:System.Convert> w<xref:System> przestrzeni nazw konwertuje`True` do + 1.  
  
 Jeśli konieczne jest przekonwertowanie `Boolean` wartości na typ danych liczbowych, należy zachować ostrożność, która metoda konwersji jest używana.  
  
## <a name="character-literal-generates-compiler-error"></a>Literał znakowy generuje błąd kompilatora  
 W przypadku braku znaków typu, Visual Basic przyjmuje domyślne typy danych dla literałów. Domyślny typ literału znakowego, ujęty w cudzysłów (`" "`) — to. `String`  
  
 Typ danych nie jest rozszerzany na [Typ danych char.](../../../../visual-basic/language-reference/data-types/char-data-type.md) `String` Oznacza to, że jeśli chcesz przypisać literał do `Char` zmiennej, musisz wykonać konwersję zwężaną lub wymusić literał dla tego `Char` typu.  

|Aby utworzyć literał char do przypisania do zmiennej lub stałej|
|---|  
|1.  Zadeklaruj zmienną lub stałą jako `Char`.<br />2.  Ujmij wartość znaku w cudzysłów (`" "`).<br />3.  Aby wymusić `C` `Char`literał, użyj znaku zamykającego podwójnego cudzysłowu z typem literału. Jest to konieczne, jeśli przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) ma `On`wartość i jest pożądany w każdym przypadku.|  
  
 Poniższy przykład ilustruje nieudane i udane przydziały literału do `Char` zmiennej.  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 Jest to zawsze ryzykowne przy użyciu wąskich konwersji, ponieważ mogą one kończyć się niepowodzeniem w czasie wykonywania. Na przykład konwersja z `String` do programu `Char` może zakończyć się niepowodzeniem `String` , jeśli wartość zawiera więcej niż jeden znak. W związku z tym lepszym rozwiązaniem jest użycie `C` znaku typu.  
  
## <a name="string-conversion-fails-at-run-time"></a>Konwersja ciągu kończy się niepowodzeniem w czasie wykonywania  
 [Typ danych ciągu](../../../../visual-basic/language-reference/data-types/string-data-type.md) uczestniczy w bardzo nielicznych konwersjach rozszerzających. `String`rozszerza `Object`tylko do siebie i, tylko `Char` i `Char()` ( `Char` tablicowe), do `String`. Wynika to z `String` faktu, że zmienne i stałe mogą zawierać wartości, które nie mogą zawierać innych typów danych.  
  
 Gdy przełącznik sprawdzania typu ([instrukcja Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) ma wartość `On`, kompilator nie zezwala na wszystkie niejawne konwersje zawężające. Dotyczy to również tych `String`, które obejmują. Kod może nadal używać słów kluczowych konwersji, takich `CStr` jak i [CType Funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), które kierują .NET Framework do próby konwersji.  
  
> [!NOTE]
> Zawężanie — błąd konwersji jest pomijany dla konwersji z elementów w `For Each…Next` kolekcji do zmiennej kontroli pętli. Aby uzyskać więcej informacji i przykładów, zobacz sekcję "Konwersje wąskie" w sekcji [for each... Next — instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zawężanie ochrony konwersji  
 Wadą konwersji zawężania jest to, że mogą one kończyć się niepowodzeniem w czasie wykonywania. Na przykład, jeśli `String` zmienna zawiera coś innego niż "true" lub "false", nie może być konwertowana na. `Boolean` Jeśli zawiera znaki interpunkcyjne, konwersja na dowolny typ liczbowy kończy się niepowodzeniem. Chyba że wiadomo, że `String` zmienna zawsze utrzymuje wartości, które typ docelowy może zaakceptować, nie należy próbować konwersji.  
  
 Jeśli trzeba skonwertować z `String` na inny typ danych, najbezpieczniejsza procedura polega na zawieszeniu próby konwersji w [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Pozwala to na poradzenie sobie z błędem czasu wykonywania.  
  
### <a name="character-arrays"></a>Tablice znaków  
 Pojedyncza `Char` i `Char` Tablica elementów rozszerzane do `String`. Jednakże nie `Char()`jest rozszerzany do. `String` Aby przekonwertować `String` wartość `Char` na tablicę <xref:System.String.ToCharArray%2A> , można <xref:System.String?displayProperty=nameWithType> użyć metody klasy.  
  
### <a name="meaningless-values"></a>Bez znaczenia wartości  
 Ogólnie rzecz biorąc `String` wartości nie są istotne w przypadku innych typów danych, a konwersja jest wysoce sztuczna i niebezpieczna. Zawsze, gdy jest to możliwe, należy `String` ograniczyć użycie zmiennych do sekwencji znaków, dla których zostały zaprojektowane. Nigdy nie należy pisać kodu, który opiera się na równoważnych wartościach w innych typach.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
