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
ms.openlocfilehash: 9bbc7f51de9899354184d051d8f1a584651dd030
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079365"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Rozwiązywanie problemów związanych z typami danych (Visual Basic)
Ta strona zawiera listę niektórych typowych problemów, które mogą wystąpić podczas wykonywania operacji na typy danych wewnętrznych.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Zmiennoprzecinkowe wyrażeń nie porównują jako równe  
 Podczas pracy z liczb zmiennoprzecinkowych ([jednego typu danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) i [typ danych Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), należy pamiętać, że są przechowywane jako ułamki binarne. Oznacza to, że nie posiadają reprezentację w postaci dokładnie dowolnej ilości, która nie jest binarny ułamek (w postaci k / (2 ^ n) gdzie k i n są liczbami całkowitymi). Na przykład 0,5 (= 1/2) i 0.3125 (= 5/16) mogą być przechowywane dokładne wartości (= 1/5) 0.2 i 0.3 (= 3/10) może być tylko przybliżeniem.  
  
 W związku z tym niedokładności, nie można polegać na dokładne wyniki podczas działania na wartości zmiennoprzecinkowe. W szczególności dwie wartości, które są równe teoretycznie może być nieco inne oświadczenia.  
  
| Aby porównać liczby zmiennoprzecinkowe | 
|---| 
|1.  Oblicz wartość bezwzględną liczby ich różnica przy użyciu <xref:System.Math.Abs%2A> metody <xref:System.Math> klasy w <xref:System> przestrzeni nazw.<br />2.  Określ dopuszczalne maksymalna różnica tak, można rozważyć dwa ilości, które mają być taka sama ze względów praktycznych, jeśli ich różnica jest większa.<br />3.  Porównanie wartości bezwzględne, różnicy, różnica dopuszczalne.|  
  
 Poniższy przykład pokazuje poprawne i niepoprawne porównanie dwóch `Double` wartości.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury tak, aby go określić dokładność lepsze niż `CStr` używa słowa kluczowego. Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza te możliwości 17 cyfr.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod — Operator nie może zwracać uzyskać dokładny wynik  
 Ze względu na niedokładności zmiennoprzecinkowych magazynu [Mod — Operator](../../../../visual-basic/language-reference/operators/mod-operator.md) po co najmniej jeden z argumentów zmiennoprzecinkowych może zwrócić nieoczekiwany wynik.  
  
 [Typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie używa odwzorowanie liczby zmiennoprzecinkowej. Liczby, które są niedokładne w `Single` i `Double` są dokładne w `Decimal` (na przykład 0.2 i 0.3). Chociaż arytmetyczny jest wolniejszy w `Decimal` niż w zmiennoprzecinkowych, może być warte obniżenie wydajności w celu osiągnięcia lepszej dokładności.  
  
|Aby znaleźć pozostałej liczby całkowitej ilości zmiennoprzecinkowych|  
|---|  
|1.  Zadeklaruj zmienne jako `Decimal`.<br />2.  Użyj znaku typu literał `D` wymusić literałów `Decimal`, w przypadku, gdy ich wartości są zbyt duże, aby `Long` typu danych.|  
  
 W poniższym przykładzie pokazano potencjał niedokładności argumentów operacji zmiennoprzecinkowej.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury tak, aby go określić dokładność lepsze niż `CStr` używa słowa kluczowego. Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza te możliwości 17 cyfr.  
  
 Ponieważ `zeroPointTwo` jest `Double`, jego wartość 0.2 jest nieskończenie powtarzające się ułamek binarne, przy użyciu przechowywaną wartość 0.20000000000000001. Podzielenie 2.0 przez ilość ta daje 9.9999999999999995 z końca 0.19999999999999991.  
  
 W wyrażeniu dla `decimalRemainder`, znak literalny typu `D` wymusza oba operandy `Decimal`, i 0.2 jej reprezentacji dokładne. W związku z tym `Mod` operator daje Oczekiwano końca 0,0.  
  
 Należy pamiętać, że nie jest wystarczające, aby zadeklarować `decimalRemainder` jako `Decimal`. Należy też wymusić literałów `Decimal`, lub używają `Double` domyślnie i `decimalRemainder` otrzymuje taką samą wartość niedokładne jak `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ wartości logicznej nie konwersji na typ liczbowy dokładnie  
 [Typ danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartości nie są przechowywane jako liczby i przechowywane wartości nie są przeznaczone do równoważne liczb. Zapewnia zgodność z wcześniejszymi wersjami, słowa kluczowe konwersji Visual Basic ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`i tak dalej) do konwersji między `Boolean` typy liczbowe. Jednak inne języki czasami wykonywaniu konwersji inaczej, tak jak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody.  
  
 Nigdy nie należy wpisać kod, który opiera się na równoważne wartości liczbowe `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są one przeznaczone. Po przemieszaniu musi `Boolean` oraz wartości liczbowych, upewnij się, że rozumiesz metodę konwersji, który wybierzesz.  
  
### <a name="conversion-in-visual-basic"></a>Konwersja w języku Visual Basic  
 Kiedy używasz `CType` lub `CBool` słowa kluczowe konwersji do konwersji liczbowych typów danych do `Boolean`, staje się 0 `False` i stają się wszystkie inne wartości `True`. Podczas konwertowania `Boolean` wartości liczbowych typów przy użyciu słowa kluczowe konwersji, `False` staje się 0 i `True` staje się -1.  
  
### <a name="conversion-in-the-framework"></a>Konwersja w ramach  
 <xref:System.Convert.ToInt32%2A> Metody <xref:System.Convert> klasy w <xref:System> konwertuje przestrzeń nazw `True` do + 1.  
  
 Jeśli musisz konwertować `Boolean` wartość zawierającą dane typu liczbowego, należy być ostrożnym o metodę konwersji, których używasz.  
  
## <a name="character-literal-generates-compiler-error"></a>Literału znakowego generuje błąd kompilatora  
 W przypadku braku znaków typu języka Visual Basic przyjęto założenie, domyślne typy danych dla literałów. Domyślny typ dla literału znakowego — ujęta w znaki cudzysłowu (`" "`) — jest `String`.  
  
 `String` Typu danych nie mogą zostać poszerzone do [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md). Oznacza to, że jeśli chcesz przypisać do literału `Char` zmiennych, musisz wprowadzić konwersji zawężającej lub literał, aby wymusić `Char` typu.  

|Aby utworzyć znaku literału można przypisać do zmiennej lub — stała|
|---|  
|1.  Zadeklaruj zmienną lub stałą jako `Char`.<br />2.  Należy wpisać wartość znaku w cudzysłowie (`" "`).<br />3.  Postępuj zgodnie z podwójnego cudzysłowu zamykającego znaku typu literał `C` literał, aby wymusić `Char`. Jest to konieczne, jeśli kontrola typów w przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, i jest pożądane w każdym przypadku.|  
  
 W poniższym przykładzie pokazano zarówno powiodło się, jak i pomyślnego przypisania literału do `Char` zmiennej.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Istnieje ryzyko przy użyciu konwersji zawężających, ponieważ może zakończyć się niepowodzeniem w czasie wykonywania. Na przykład konwersja `String` do `Char` może zakończyć się niepowodzeniem, jeśli `String` wartość zawiera więcej niż jeden znak. W związku z tym, lepiej jest programowania do użycia `C` wpisz znak.  
  
## <a name="string-conversion-fails-at-run-time"></a>Konwersja ciągu nie powiedzie się w czasie wykonywania  
 [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) uczestniczy w bardzo nielicznych konwersje rozszerzające. `String` rozszerza się tylko do samego siebie i `Object`i tylko `Char` i `Char()` ( `Char` tablicy) mogą zostać poszerzone do `String`. Jest to spowodowane `String` zmiennych i stałych może zawierać wartości, które nie mogą zawierać inne typy danych.  
  
 Podczas sprawdzania typu przełącznika ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, kompilator nie zezwala na wszystkie niejawne konwersje zawężające. Obejmuje to te, które są obejmujące `String`. Kod można nadal używać słowa kluczowe konwersji takich jak `CStr` i [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), które bezpośrednio [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] próby konwersji.  
  
> [!NOTE]
>  Błąd konwersji zawężających jest pomijana dla konwersji z elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli. Aby uzyskać więcej informacji i przykładów, zobacz sekcję "Konwersje zawężające" w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zawężanie konwersji ochrony  
 Wadą konwersji zawężających jest, że może działać w czasie wykonywania. Na przykład jeśli `String` zmienna zawiera coś innego niż "True" lub "Fałsz", nie można przekonwertować na `Boolean`. Zawiera on znaki interpunkcyjne, konwersja do dowolnego typu liczbowego kończy się niepowodzeniem. O ile nie wiesz, że Twoje `String` zmienna zawsze zawiera wartości, które może akceptować docelowy typ, nie należy spróbować konwersji.  
  
 Jeśli musisz konwertować z `String` na inny typ danych jest ujęcie próba konwersji w najbezpieczniejszym procedury [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Dzięki temu można dotyczy błąd czasu wykonywania.  
  
### <a name="character-arrays"></a>Tablice znaków  
 Pojedynczy `Char` oraz tablicę `Char` elementy, które obie mogą zostać poszerzone do `String`. Jednak `String` nie mogą zostać poszerzone do `Char()`. Aby przekonwertować `String` wartość `Char` tablicy, możesz użyć <xref:System.String.ToCharArray%2A> metody <xref:System.String?displayProperty=nameWithType> klasy.  
  
### <a name="meaningless-values"></a>Ta nie ma znaczenia wartości  
 Ogólnie rzecz biorąc `String` wartości nie są istotne w przypadku innych typów danych i konwersji jest niezwykle sztuczny i niebezpieczne. Jeśli to możliwe, należy ograniczyć użycie `String` zmienne sekwencji znaków, dla których są one przeznaczone. Nigdy nie należy napisać kod, który opiera się na równoważne wartości w innych typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
