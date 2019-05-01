---
title: Option Strict — instrukcja (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8547e8e1eaf73b266d737e33acd79dd4ec539c6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051172"
---
# <a name="option-strict-statement"></a>Option Strict — Instrukcja
Ogranicza niejawne konwersje typów danych można tylko konwersje rozszerzające nie zezwalają na późne wiązanie i nie zezwalają na niejawnego wpisywania, które spowodowało, że `Object` typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalna. Włącza `Option Strict` sprawdzania.|  
|`Off`|Opcjonalna. Wyłącza `Option Strict` sprawdzania.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Strict On` lub `Option Strict` pojawia się w pliku, następujące warunki spowodować błąd kompilacji:  
  
- Niejawne konwersje zawężające  
  
- Późne powiązania  
  
- Niejawnego wpisywania, które spowodowało, że `Object` typu  
  
> [!NOTE]
>  W konfiguracji ostrzeżeń, które można ustawić na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), dostępne są trzy ustawienia, które odnoszą się do trzech warunków, które powodują błąd kompilacji. Aby uzyskać informacje o sposobie używania tych ustawień, zobacz [do ustawienia konfiguracje ostrzeżenie w środowisku IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) w dalszej części tego tematu.  
  
 `Option Strict Off` Instrukcji wyłącza błąd i ostrzeżenie sprawdzania pod kątem wszystkich trzech warunków, nawet jeśli określone skojarzone ustawienia IDE, aby włączyć te błędy lub ostrzeżenia. `Option Strict On` Instrukcji włącza błędów i ostrzeżeń sprawdzania pod kątem wszystkich trzech warunków, nawet jeśli określone skojarzone ustawienia IDE, aby wyłączyć te błędy lub ostrzeżenia.  
  
 Jeśli używane, `Option Strict` instrukcja musi występować przed wszystkimi instrukcjami kod w pliku.  
  
 Po ustawieniu `Option Strict` do `On`, Visual Basic sprawdza, czy typy danych są określone dla wszystkich elementów programowania. Typy danych mogą być jawnie określone lub określone za pomocą wnioskowanie o typie lokalnym. Określanie typów danych dla wszystkich elementów programowania jest zalecane, z następujących powodów:  
  
- Umożliwia obsługę funkcji IntelliSense dla zmiennych i parametrów. Dzięki temu można zobaczyć ich właściwości i inne elementy członkowskie podczas pisania kodu.  
  
- Umożliwia kompilatorowi wykonywanie sprawdzania typu. Kontrola typów pomoże Ci znaleźć instrukcje, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów konwersji typu. Określa on wywołania metod obiektów, które nie obsługują tych metod.  
  
- Przyspiesza wykonywanie kodu. Co dzieje się, jeśli nie określisz typ danych dla elementu programistycznego, kompilator Visual Basic przypisuje mu `Object` typu. Skompilowany kod może być konieczne konwersji do i z powrotem między `Object` a innymi typami danych, które powoduje zmniejszenie wydajności.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Niejawne błędy konwersji zawężającej  
 Niejawne błędy konwersji zawężającej wystąpić, gdy jest konwersja typu danych niejawne, który jest konwersją zawężającą.  
  
 Język Visual Basic można przekonwertować wiele typów danych na inne typy danych. Może wystąpić utrata danych, gdy wartość jednego typu danych jest konwertowany na typ danych, który ma mniejszą dokładność lub mniejszą pojemność. Błąd czasu wykonywania występuje, jeśli konwersja zawężająca zakończy się niepowodzeniem. `Option Strict` zapewnia kompilacji powiadomienia o tych konwersji zawężających, dzięki czemu można uniknąć. Aby uzyskać więcej informacji, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) i [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Konwersje, które mogą powodować błędy zawierają niejawne konwersje, które występują w wyrażeniach. Więcej informacji znajduje się w następujących tematach:  
  
- [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Podczas łączenia ciągów za pomocą [& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), wszystkie konwersje do ciągów są uznawane za się rozszerzenia. Dzięki takiej konwersji nie generują niejawne błąd konwersji zawężających, nawet jeśli `Option Strict` znajduje się na.  
  
 Po wywołaniu metody, która ma argument, który ma typ danych różni się od odpowiedniego parametru konwersji zawężającej powoduje błąd w czasie kompilacji, jeśli `Option Strict` znajduje się na. Aby uniknąć tego błędu kompilacji, należy za pomocą konwersji rozszerzającej lub jawną konwersję.  
  
 Niejawne błędy konwersji zawężającej są pomijane w czasie kompilacji w przypadku konwersji z typu elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli. Dzieje się tak nawet wtedy, gdy `Option Strict` znajduje się na. Aby uzyskać więcej informacji, zobacz sekcję "Konwersje zawężające" w [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Późne wiązanie błędy  
 Obiekt jest rozpoznanie późnego wiązania, gdy jest ona przypisana do właściwości lub metody w zmiennej, która jest zadeklarowana jako typ `Object`. Aby uzyskać więcej informacji, zobacz [wczesnego a późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Błędy typu obiektu niejawne  
 Niejawne obiektu typu błędy występują, gdy odpowiedni typ nie może być wywnioskowane dla zadeklarowanej zmiennej, więc typ `Object` została wywnioskowana. To przede wszystkim występuje, gdy używasz `Dim` instrukcję, aby zadeklarować zmienną bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Parametry metody `As` klauzula jest opcjonalny Jeśli `Option Strict` jest wyłączona. Jednak jeśli korzysta z żadnych jeden parametr `As` klauzuli, wszystkie one musisz ją wykorzystać. Jeśli `Option Strict` jest włączona, `As` klauzula jest wymagana dla każdej definicji parametru.  
  
 Jeśli zmienna jest zadeklarowana bez użycia `As` klauzuli i ustaw ją na `Nothing`, zmienna posiada typ `Object`. Błąd kompilacji nie występuje w tym przypadku podczas `Option Strict` znajduje się na i `Option Infer` znajduje się na. Na przykład `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Dane domyślne typy i wartości  
 W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Określony typ danych?|Inicjatora określona?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd kompilacji.|  
|Nie|Yes|`Dim qty = 5`|Jeśli `Option Infer` znajduje się na (ustawienie domyślne), zmienna przyjmuje dane typu inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączone, zmienna ma typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest ustawiana na wartość domyślną dla typu danych. Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Tak|Yes|`Dim qty  As Integer = 5`|Jeśli typ danych Inicjator nie jest konwertowany na określony typ danych, wystąpi błąd kompilacji.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Jeśli nie jest obecny Option Strict — instrukcja  
 Jeśli kod źródłowy nie zawiera `Option Strict` instrukcji **opcja strict** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany. **Kompiluj stronę** ma ustawienia, które zapewniają dodatkową kontrolę nad warunki, które generuje błąd.  
  
 Jeśli używasz kompilatora wiersza polecenia, możesz użyć [/optionstrict —](../../../visual-basic/reference/command-line-compiler/optionstrict.md) opcję kompilatora, aby określić ustawienie `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Aby ustawić Option Strict w środowisku IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. W **Eksploratora rozwiązań**, wybierz projekt. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Na **skompilować** kartę, należy ustawić wartość w **Option Strict** pole.  
  
### <a name="conditions"></a> Aby ustawić konfiguracje ostrzeżenie w środowisku IDE  
 Kiedy używasz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) zamiast `Option Strict` instrukcji, masz dodatkową kontrolę nad warunki, które generują błędy. **Konfiguracje ostrzeżenie** części **kompilowania strony** ma ustawienia, które odnoszą się do trzech warunków, które powodują błąd kompilacji podczas `Option Strict` znajduje się na. Te ustawienia są następujące:  
  
- **Niejawna konwersja**  
  
- **Rozpoznanie późnego wiązania; Wywołanie może się nie powieść w czasie wykonywania**  
  
- **Niejawne typu; założono, że obiekt**  
  
 Po ustawieniu **Option Strict** do **na**, wszystkie trzy ustawienia konfiguracji tych ostrzeżeń są ustawione na **błąd**. Po ustawieniu **Option Strict** do **poza**, wszystkie trzy ustawienia są ustawione na **Brak**.  
  
 Można zmienić indywidualnie każdy ostrzeżenie ustawienia konfiguracji **Brak**, **ostrzeżenie**, lub **błąd**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżenia są ustawione na **błąd**, `On` pojawia się w `Option strict` pole. Jeśli wszystkie trzy **Brak**, `Off` pojawia się w tym polu. Dla dowolnej kombinacji tych ustawień **(niestandardowy)** pojawia się.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Aby skonfigurować ustawienie Option Strict domyślne dla nowych projektów  
 Podczas tworzenia projektu, **Option Strict** ustawienie **skompilować** karta jest ustawiona na **Option Strict** w **opcje** okno dialogowe.  
  
 Aby ustawić `Option Strict` w tym oknie na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**. Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Aby ustawić Option Strict, w wierszu polecenia  
 Obejmują [/optionstrict —](../../../visual-basic/reference/command-line-compiler/optionstrict.md) w — opcja kompilatora **vbc** polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano błędy w czasie kompilowania spowodowany niejawnej konwersji typów, które są konwersji zawężających. Odnosi się do tej kategorii błędów **niejawna konwersja** warunku na **Kompiluj stronę**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje błąd kompilacji, spowodowane późnym wiązaniu. Odnosi się do tej kategorii błędów **najpóźniejsze powiązanie; wywołanie może się nie powieść w czasie wykonywania** warunku na **Kompiluj stronę**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano błędów spowodowanych przez zmienne, które są zadeklarowane z typem niejawne `Object`. Odnosi się do tej kategorii błędów **niejawnego typu; założono, że obiekt** warunku na **Kompiluj stronę**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Instrukcje: Dostęp do elementów członkowskich obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Późne powiązania w rozwiązaniach pakietu Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
