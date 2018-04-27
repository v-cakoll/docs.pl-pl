---
title: Rozwiązywanie problemów związanych z typami danych (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f34e7bc50a51032387cf01db3fae17ef44b8b4d9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-data-types-visual-basic"></a>Rozwiązywanie problemów związanych z typami danych (Visual Basic)
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas wykonywania operacji na typy danych wewnętrznych.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Zmiennoprzecinkowe wyrażenia porównuje jako równe  
 Podczas pracy z liczb zmiennoprzecinkowych ([jednego typu danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) i [— typ danych Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), należy pamiętać, że są one przechowywane jako binarne ułamków. Oznacza to, że nie posiadają dokładną reprezentację żadnych ilość, która nie jest binarny ułamek (w postaci k / (2 ^ n) gdzie k i n są liczbami całkowitymi). Na przykład 0,5 (= 1/2) i 0.3125 (= 5/16) może być przechowywany jako dokładne wartości, 0,2 (= 1/5) i 0,3 (= 3/10) może być tylko przybliżeniem.  
  
 W związku z tym błędu, możesz nie zależą od dokładne wyniki podczas działania na wartości zmiennoprzecinkowe. W szczególności dwie wartości, które są równe teoretycznie może być nieco inne oświadczenia.  
  
| Aby porównać liczb zmiennoprzecinkowych | 
|---| 
|1.  Obliczyć wartość bezwzględna różnica ich przy użyciu <xref:System.Math.Abs%2A> metody <xref:System.Math> klasy w <xref:System> przestrzeni nazw.<br />2.  Określ dopuszczalne maksymalnego różnica taki sposób, że należy wziąć pod uwagę dwa ilości, które mają być taka sama dla celów praktycznych, jeśli ich różnica jest nie większy.<br />3.  Porównanie wartości bezwzględne różnicy dopuszczalne różnicy.|  
  
 W poniższym przykładzie pokazano zarówno nieprawidłowych i poprawne porównanie dwóch `Double` wartości.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury, dzięki czemu można określić większą dokładność niż `CStr` używa słowa kluczowego. Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza on 17 cyfr.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod — Operator nie zwraca wyniku dokładne  
 Z powodu błędu zmiennoprzecinkowe magazynu [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md) może zwrócić nieoczekiwany wynik, gdy co najmniej jeden z argumentów jest zmiennoprzecinkowych.  
  
 [Typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie używa odwzorowanie liczby zmiennoprzecinkowej. Liczby, które są niedokładnymi w `Single` i `Double` są dokładnie w `Decimal` (na przykład 0.2 i 0,3). Mimo że arytmetyczne działa wolniej w `Decimal` niż w liczb zmiennoprzecinkowych, może być warto obniżenie wydajności w celu osiągnięcia lepszej dokładności.  
  
|Aby znaleźć pozostałej liczby całkowitej ilości liczb zmiennoprzecinkowych|  
|---|  
|1.  Zadeklaruj zmienne jako `Decimal`.<br />2.  Znak literalny typu `D` wymusić literały do `Decimal`, w przypadku, gdy ich wartości są za szerokie dla `Long` — typ danych.|  
  
 W poniższym przykładzie pokazano ryzyko błędu argumentów operacji zmiennoprzecinkowej.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury, dzięki czemu można określić większą dokładność niż `CStr` używa słowa kluczowego. Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza on 17 cyfr.  
  
 Ponieważ `zeroPointTwo` jest `Double`, jego wartość 0,2 jest nieskończenie identycznych ułamek binarnego z wartością przechowywaną 0.20000000000000001. Podzielenie 2.0 przez ilość ta daje 9.9999999999999995 pozostałych 0.19999999999999991.  
  
 W wyrażeniu dla `decimalRemainder`, znak literalny typu `D` wymusza oba argumenty do `Decimal`, i 0,2 ma reprezentację dokładne. W związku z tym `Mod` operatora daje Oczekiwano końca 0,0.  
  
 Należy pamiętać, że nie jest wystarczające, aby zadeklarować `decimalRemainder` jako `Decimal`. Należy też wymusić literały do `Decimal`, lub wykorzystują `Double` domyślnie i `decimalRemainder` odbiera tę samą wartość niedokładne jako `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Typ Boolean nie konwertować na typ liczbowy dokładnie  
 [Boolean — typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartości nie są przechowywane jako liczby i przechowywane wartości nie są przeznaczone do równoważne cyfry. Dla zachowania zgodności z wcześniejszymi wersjami programu Visual Basic zawiera słowa kluczowe konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`i tak dalej) umożliwia konwersję pomiędzy `Boolean` typy liczbowe. Jednak inne języki czasem wykonywania tych konwersji inaczej, tak jak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody.  
  
 Nigdy nie powinien pisania kodu, który polega na równoważne wartości numerycznych `True` i `False`. Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są przeznaczone. Jeśli musisz mieszać `Boolean` i wartości liczbowe, upewnij się, że rozumiesz wybranej metody konwersji.  
  
### <a name="conversion-in-visual-basic"></a>Konwersja w języku Visual Basic  
 Jeśli używasz `CType` lub `CBool` słowa kluczowe konwersji do konwersji liczbowych typów danych do `Boolean`, staje się 0 `False` i stać się wszystkie inne wartości `True`. Podczas konwertowania `Boolean` wartości na typy liczbowe za pomocą słowa kluczowe konwersji, `False` staje się 0 i `True` staje się wartość -1.  
  
### <a name="conversion-in-the-framework"></a>Konwersja w ramach  
 <xref:System.Convert.ToInt32%2A> Metody <xref:System.Convert> klasy w <xref:System> konwertuje przestrzeń nazw `True` do + 1.  
  
 Jeśli trzeba przekonwertować `Boolean` wartości na dane typu liczbowego, należy zachować ostrożność o wyborze metody konwersji używasz.  
  
## <a name="character-literal-generates-compiler-error"></a>Literał znaku generuje błąd kompilatora  
 W przypadku braku znaków typu Visual Basic zakłada domyślne typy danych dla literałów. Domyślny typ literał znakowy — ujęta w znaki cudzysłowu (`" "`) — jest `String`.  
  
 `String` — Typ danych nie są rozszerzane [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md). Oznacza to, że jeśli chcesz przypisać literał do `Char` zmiennej, należy dokonać konwersji zawężającej lub wymusić literał do `Char` typu.  

|Aby utworzyć literał można przypisać do zmiennej lub stała wartość typu Char|
|---|  
|1.  Deklarowanie zmiennej lub stała jako `Char`.<br />2.  Należy wpisać wartość znaku w cudzysłowie (`" "`).<br />3.  Wykonaj podwójnego cudzysłowu zamykającego znak literalny typu `C` wymusić literał do `Char`. Jest to konieczne, jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, i jest pożądane w każdym przypadku.|  
  
 W poniższym przykładzie pokazano przypisania nie powiodło się jak pomyślnie literału do `Char` zmiennej.  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Istnieje ryzyko za pomocą konwersji zawężającej, ponieważ może zakończyć się niepowodzeniem w czasie wykonywania. Na przykład konwersji `String` do `Char` może zakończyć się niepowodzeniem, jeśli `String` wartość zawiera więcej niż jeden znak. W związku z tym lepiej jest programowania do użycia `C` znaku typu.  
  
## <a name="string-conversion-fails-at-run-time"></a>Konwersja ciągu nie powiedzie się w czasie wykonywania  
 [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) uczestniczy w bardzo mało poszerzanie konwersji. `String` rozszerzenie tylko do samego siebie i `Object`i tylko `Char` i `Char()` ( `Char` tablicy) rozszerzane `String`. Jest to spowodowane `String` zmiennych i stałych może zawierać wartości, które nie mogą zawierać inne typy danych.  
  
 Podczas sprawdzania typu przełącznika ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, kompilator nie zezwala na wszystkich niejawnej konwersji zawężającej. Obejmuje to te obejmujące `String`. Kod można nadal używać słowa kluczowe konwersji takich jak `CStr` i [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), które bezpośrednio [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] próby konwersji.  
  
> [!NOTE]
>  Błąd zawężanie konwersji jest pomijane w przypadku konwersji z typu elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli for. Aby uzyskać dodatkowe informacje i przykłady, zobacz sekcję "Zawężanie konwersji" w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Zawężanie konwersji ochrony  
 Zawężanie konwersji wadą jest to, że ich może zakończyć się niepowodzeniem w czasie wykonywania. Na przykład jeśli `String` zmiennej zawiera coś innego niż "Prawda" lub "Fałsz", nie można przekonwertować na `Boolean`. Jeśli zawiera znaki interpunkcyjne, konwersji do dowolnego typu liczbowego kończy się niepowodzeniem. Jeśli nie wiesz, że Twoje `String` zmienna zawsze przechowuje wartości, które może zaakceptować docelowego, nie należy spróbować konwersji.  
  
 Jeśli muszą być konwertowane z `String` na inny typ danych ma ujmij próba konwersji w możliwie najbezpieczniejszy procedura [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Dzięki temu można rozwiązać błąd czasu wykonywania.  
  
### <a name="character-arrays"></a>Tablice znaków  
 Pojedynczy `Char` i tablica `Char` elementy zarówno rozszerzane `String`. Jednak `String` nie rozszerzane `Char()`. Aby przekonwertować `String` do wartości `Char` tablicy, można użyć <xref:System.String.ToCharArray%2A> metody <xref:System.String?displayProperty=nameWithType> klasy.  
  
### <a name="meaningless-values"></a>Znaczenia wartości  
 Ogólnie rzecz biorąc `String` wartości nie są przydatne w przypadku innych typów danych, a konwersja jest wysoce sztuczne i niebezpieczne. Jeśli to możliwe, należy ograniczyć użycie `String` zmienne sekwencji znaków, dla których są przeznaczone. Nigdy nie powinien pisania kodu, który polega na równoważne wartości w innych typach.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Skuteczne stosowanie typów danych](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
