---
title: "Option Strict — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 238f64001b097b86306e0ed9630bd5df2e6a189f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="option-strict-statement"></a>Option Strict — Instrukcja
Ogranicza niejawne konwersje typów danych można tylko rozszerzanie konwersji, uniemożliwia późne wiązanie i nie zezwala na niejawne wpisanie, który daje w `Object` typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalny. Włącza `Option Strict` sprawdzania.|  
|`Off`|Opcjonalny. Wyłącza `Option Strict` sprawdzania.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Strict On` lub `Option Strict` pojawia się w pliku, błąd kompilacji powodują następujące warunki:  
  
-   Niejawne konwersje zawężającej  
  
-   Późne powiązania  
  
-   Niejawne wpisanie, który daje w `Object` typu  
  
> [!NOTE]
>  W konfiguracji ostrzeżeń, które można ustawić na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), dostępne są trzy ustawienia, które odpowiadają trzy warunki, które spowodować błąd kompilacji. Aby uzyskać informacje o sposobie używania tych ustawień, zobacz [do ustawienia konfiguracje ostrzeżenie w IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) dalszej części tego tematu.  
  
 `Option Strict Off` Instrukcji wyłącza błąd i ostrzeżenie sprawdzanie dla wszystkich trzech warunków, nawet jeśli określone powiązane ustawienia IDE, aby włączyć te błędy lub ostrzeżenia. `Option Strict On` Instrukcji włącza błąd i ostrzeżenie sprawdzania dla wszystkich trzech warunków, nawet jeśli skojarzone ustawienia IDE określają, aby wyłączyć te błędy lub ostrzeżenia.  
  
 Jeśli używana, `Option Strict` instrukcji musi występować przed wszystkimi instrukcjami kodu w pliku.  
  
 Podczas ustawiania `Option Strict` do `On`, Visual Basic sprawdza, czy typy danych są określone dla wszystkich elementów programowania. Typy danych mogą być określone jawnie lub określony za pomocą wnioskowanie o typie lokalnym. Określanie typów danych dla wszystkich elementów programowania jest zalecane, z następujących powodów:  
  
-   Umożliwia obsługę funkcji IntelliSense na parametry i zmienne. Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich pisania kodu.  
  
-   Umożliwia kompilatorowi sprawdzania typu. Sprawdzanie typu ułatwia instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów konwersji typu. Identyfikuje wywołań metod obiektów, które nie obsługują tych metod.  
  
-   Przyspieszenie wykonywania kodu. Powodem tego jest, że jeśli nie określisz typu danych dla elementu programistycznego, kompilator Visual Basic przypisuje go `Object` typu. Skompilowany kod może być konieczne Konwertuj i z powrotem między `Object` a innymi typami danych, co zmniejsza wydajność.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Niejawne błędy konwersji zawężającej  
 Niejawne błędy konwersji zawężającej wystąpić, gdy istnieje konwersja typu danych niejawne, który jest konwersji zawężającej.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]można przekonwertować wiele typów danych na inne typy danych. Może wystąpić utrata danych, gdy wartość jednego typu danych jest konwertowana na typ danych, który ma mniej precyzję lub mniejszą pojemność. Błąd czasu wykonywania występuje, jeśli konwersji zawężającej nie powiedzie się. `Option Strict`zapewnia powiadomień kompilacji tych konwersji zawężającej, dzięki czemu można uniknąć. Aby uzyskać więcej informacji, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) i [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Konwersje, które mogą powodować błędy obejmują niejawne konwersje, które występują w wyrażeniach. Więcej informacji znajduje się w następujących tematach:  
  
-   [+ — Operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [+= — Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [CHAR — typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Podczas łączenia ciągów za pomocą [& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), wszystkie konwersji na ciągi są uważane za można rozszerzanie. Dlatego te konwersje nie generują niejawne błąd konwersji zawężającej, nawet jeśli `Option Strict` znajduje się na.  
  
 Po wywołaniu metody, która ma argument o typie danych inne niż odpowiadającego mu parametru konwersji zawężającej powoduje błąd kompilacji w przypadku `Option Strict` znajduje się na. Błąd kompilacji można uniknąć, używając konwersję rozszerzającą lub jawnej konwersji.  
  
 Niejawne błędy konwersji zawężającej są pomijane w czasie kompilacji w przypadku konwersji z typu elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli for. Dzieje się tak nawet wtedy, gdy `Option Strict` znajduje się na. Aby uzyskać więcej informacji, zobacz sekcję "Zawężanie konwersji" w [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Późne wiązanie błędów  
 Obiekt jest późnym wiązaniem, gdy jest przypisany do właściwości lub metody zmienna, która jest zadeklarowana jako typu `Object`. Aby uzyskać więcej informacji, zobacz [wczesnego i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Błędy typów obiektu niejawne  
 Niejawne obiektu typu błędy występują, gdy nie może być odpowiedniego typu wywnioskowane dla zadeklarowana zmienna, więc typ `Object` jest wywnioskowany. To przede wszystkim występuje, gdy używasz `Dim` instrukcji, aby zadeklarować zmienną bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Parametry metody `As` jest opcjonalna klauzula Jeśli `Option Strict` jest wyłączona. Jednak jeśli korzysta z żadnych jeden parametr `As` klauzuli, wszystkie muszą używać go. Jeśli `Option Strict` , `As` klauzula jest wymagany dla każdej definicji parametru.  
  
 Jeśli zmienna jest zadeklarowana bez użycia `As` klauzuli i ustaw ją na `Nothing`, zmienna ma typ `Object`. Błędy kompilacji nie będą występować w tym przypadku jeśli `Option Strict` znajduje się na i `Option Infer` znajduje się na. Na przykład jest `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Dane domyślne typy i wartości  
 W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Określony typ danych?|Inicjator określona?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.|  
|Nie|Tak|`Dim qty = 5`|Jeśli `Option Infer` znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Jeśli nie jest obecny Option Strict — instrukcja  
 Jeśli kod źródłowy nie zawiera `Option Strict` instrukcji, **opcja strict** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. **Skompilować strony** zawiera ustawienia, które zapewniają dodatkową kontrolę nad warunki, które generuje błąd.  
  
 Jeśli używasz kompilatora wiersza polecenia, można użyć [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) opcję kompilatora, aby określić ustawienie `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Aby ustawić Option Strict w środowisku IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Na **skompilować** ustaw wartość **Option Strict** pole.  
  
###  <a name="conditions"></a>Aby ustawić konfiguracje ostrzeżenie w środowisku IDE  
 Jeśli używasz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) zamiast `Option Strict` instrukcji, masz dodatkową kontrolę nad warunki, które generują błędy. **Konfiguracje ostrzeżenie** sekcji **skompilować strony** zawiera ustawienia, które odpowiadają trzy warunki, które spowodować błąd kompilacji podczas `Option Strict` znajduje się na. Te ustawienia są następujące:  
  
-   **Niejawna konwersja**  
  
-   **Późne wiązanie; Wywołanie może zakończyć się niepowodzeniem w czasie wykonywania**  
  
-   **Niejawne typu. założono, że obiekt**  
  
 Podczas ustawiania **Option Strict** do **na**, wszystkie trzy ustawienia konfiguracji tych ostrzeżeń są ustawione na **błąd**. Podczas ustawiania **Option Strict** do **poza**, wszystkie trzy ustawienia **Brak**.  
  
 Oddzielnie można zmienić ustawienie konfiguracji każdego ostrzeżenie **Brak**, **ostrzeżenie**, lub **błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenie **błąd**, `On` pojawia się w `Option strict` pole. Jeśli wszystkie trzy **Brak**, `Off` pojawia się w tym polu. Dla dowolnej kombinacji tych ustawień **(niestandardowy)** pojawi się.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Aby określić ustawienie Option Strict domyślne dla nowych projektów  
 Podczas tworzenia projektu, **Option Strict** ustawienie **skompilować** ustawiono kartę **Option Strict** w **opcje** okno dialogowe.  
  
 Aby ustawić `Option Strict` w tym oknie dialogowym, na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**. Ustawieniem domyślnym początkowej w **domyślne VB** jest `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Aby ustawić Option Strict w wierszu polecenia  
 Obejmują [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano spowodowane niejawne konwersje typów, które są zawężanie konwersji błędy kompilacji. Ta kategoria błędy odpowiada **niejawna konwersja** warunku w **skompilować strony**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to błąd kompilacji spowodowane późne wiązanie. Ta kategoria błędy odpowiada **najpóźniejsze wiązanie; wywołanie może zakończyć się niepowodzeniem w czasie wykonywania** warunku w **skompilować strony**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano błędów spowodowanych przez zmienne, które są zadeklarowane z typem niejawne `Object`. Ta kategoria błędy odpowiada **typu niejawnego; założono, że obiekt** warunku w **skompilować strony**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Porady: dostęp do elementów członkowskich obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Późne wiązania w rozwiązaniach pakietu Office](https://msdn.microsoft.com/library/3xxe951d)  
 [/ optionstrict —](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
