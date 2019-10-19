---
title: Option Strict — Instrukcja (Visual Basic)
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
ms.openlocfilehash: afe2181e031a651767e6a6eec0397300b03fce50
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582570"
---
# <a name="option-strict-statement"></a>Option Strict — Instrukcja
Ogranicza niejawne konwersje typów danych tylko w celu poszerzenia konwersji, nie zezwala na późne wiązanie i nie zezwala na niejawne wpisywanie w wyniku `Object` typu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalny. Włącza sprawdzanie `Option Strict`.|  
|`Off`|Opcjonalny. Wyłącza sprawdzanie `Option Strict`.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Strict On` lub `Option Strict` pojawia się w pliku, następujące warunki powodują błąd czasu kompilacji:  
  
- Niejawne konwersje zawężające  
  
- Późne wiązanie  
  
- Niejawne wpisanie powoduje, że typ `Object`  
  
> [!NOTE]
> W konfiguracjach ostrzeżeń, które można ustawić na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), istnieją trzy ustawienia odpowiadające trzem warunkom, które powodują błąd w czasie kompilacji. Informacje o sposobach korzystania z tych ustawień znajdują [się w sekcji Aby ustawić konfiguracje ostrzeżeń w środowisku IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) w dalszej części tego tematu.  
  
 Instrukcja `Option Strict Off` wyłącza wykrywanie błędów i ostrzeżeń dla wszystkich trzech warunków, nawet jeśli skojarzone ustawienia IDE określają, czy te błędy lub ostrzeżenia mają zostać włączone. Instrukcja `Option Strict On` włącza kontrolę błędów i ostrzeżeń dla wszystkich trzech warunków, nawet jeśli skojarzone ustawienia IDE określają, aby wyłączyć te błędy lub ostrzeżenia.  
  
 Jeśli jest używana, instrukcja `Option Strict` musi znajdować się przed innymi instrukcjami kodu w pliku.  
  
 Po ustawieniu `Option Strict` na `On`, Visual Basic sprawdza, czy typy danych są określone dla wszystkich elementów programistycznych. Typy danych można określić jawnie lub określić za pomocą wnioskowania typu lokalnego. Zaleca się określenie typów danych dla wszystkich elementów programistycznych, z następujących powodów:  
  
- Umożliwia obsługę technologii IntelliSense dla zmiennych i parametrów. Dzięki temu można zobaczyć swoje właściwości i innych członków podczas wpisywania kodu.  
  
- Umożliwia kompilatorowi wykonywanie kontroli typu. Sprawdzanie typu ułatwia znalezienie instrukcji, które mogą zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów konwersji typu. Identyfikuje także wywołania metod dla obiektów, które nie obsługują tych metod.  
  
- Przyspiesza wykonywanie kodu. Jedną z przyczyn tego problemu jest to, że jeśli nie określisz typu danych dla elementu programistycznego, kompilator Visual Basic przypisze `Object` typ. Skompilowany kod może wymagać konwersji z powrotem między `Object` i innymi typami danych, co zmniejsza wydajność.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Niejawne Zawężanie błędów konwersji  
 Niejawne Zawężanie błędów konwersji występuje, gdy istnieje niejawna konwersja typu danych, która jest konwersją zawęża.  
  
 Visual Basic można skonwertować wiele typów danych na inne typy danych. Utrata danych może wystąpić, gdy wartość jednego typu danych jest konwertowana na typ danych o mniejszej dokładności lub mniejszej pojemności. Błąd czasu wykonywania występuje, gdy taka konwersja nie powiedzie się. `Option Strict` zapewnia powiadomienie czasu kompilowania tych konwersji zawężających, aby można je było uniknąć. Aby uzyskać więcej informacji, zobacz [konwersje niejawne i jawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) oraz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Konwersje, które mogą spowodować błędy, zawierają niejawne konwersje występujące w wyrażeniach. Więcej informacji znajduje się w następujących tematach:  
  
- [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [Operator/= (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Podczas łączenia ciągów przy użyciu [operatora &](../../../visual-basic/language-reference/operators/concatenation-operator.md)wszystkie konwersje do ciągów są uznawane za rozszerzające. W związku z tym konwersje nie generują niejawnego zawężanego błędu konwersji, nawet jeśli `Option Strict` jest włączona.  
  
 Gdy wywoływana jest metoda, która ma argument, który ma typ danych różny od odpowiedniego parametru, konwersja zawęża powoduje błąd czasu kompilacji, jeśli `Option Strict` jest włączona. Można uniknąć błędów czasu kompilacji przy użyciu konwersji rozszerzającej lub jawnej konwersji.  
  
 Niejawne Zawężanie błędów konwersji jest pomijane w czasie kompilacji w przypadku konwersji z elementów w kolekcji `For Each…Next` do zmiennej kontroli pętli. Dzieje się tak nawet wtedy, gdy `Option Strict` jest włączona. Aby uzyskać więcej informacji, zobacz sekcję "Konwersje wąskie" w [dla każdego... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Błędy późnego wiązania  
 Obiekt jest późnie powiązany, gdy jest przypisany do właściwości lub metody zmiennej, która jest zadeklarowana jako typu `Object`. Aby uzyskać więcej informacji, zobacz [wczesne i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Niejawne błędy typu obiektu  
 Niejawne błędy typu obiektu występują, gdy nie można wywnioskować odpowiedniego typu dla zadeklarowanej zmiennej, więc typ `Object` jest wywnioskowany. Dzieje się tak głównie w przypadku używania instrukcji `Dim` do deklarowania zmiennej bez użycia klauzuli `As`, a `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [Specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 W przypadku parametrów metody klauzula `As` jest opcjonalna, jeśli `Option Strict` jest wyłączona. Jeśli jednak którykolwiek z parametrów używa klauzuli `As`, wszystkie muszą z niej korzystać. Jeśli `Option Strict` jest włączona, klauzula `As` jest wymagana dla każdej definicji parametru.  
  
 Jeśli deklarujesz zmienną bez użycia klauzuli `As` i ustawisz ją na `Nothing`, zmienna ma typ `Object`. W tym przypadku nie występuje błąd czasu kompilacji, gdy `Option Strict` jest włączona i `Option Infer` jest włączona. Przykładem tego jest `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Domyślne typy danych i wartości  
 W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Określono typ danych?|Określono inicjator?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (wartość domyślna), zmienna jest ustawiona na `Nothing`.<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|  
|Nie|Tak|`Dim qty = 5`|Jeśli `Option Infer` jest włączone (wartość domyślna), zmienna Pobiera typ danych inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączone i `Option Strict` jest wyłączone, zmienna Pobiera typ danych `Object`.<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|  
|Tak|Nie|`Dim qty As Integer`|Zmienna jest inicjowana do wartości domyślnej dla typu danych. Aby uzyskać więcej informacji, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Gdy nie ma instrukcji Option Strict  
 Jeśli kod źródłowy nie zawiera instrukcji `Option Strict`, używane jest ustawienie **Option Strict** na [stronie kompilowania, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . **Strona kompilacja** zawiera ustawienia, które zapewniają dodatkową kontrolę nad warunkami, które generują błąd.  
  
 Jeśli używasz kompilatora wiersza polecenia, możesz użyć opcji kompilatora [/optionstrict —](../../../visual-basic/reference/command-line-compiler/optionstrict.md) , aby określić ustawienie dla `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Aby ustawić ustawienie Option Strict w środowisku IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. W **Eksplorator rozwiązań**wybierz projekt. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Na karcie **Kompilowanie** ustaw wartość w polu **Option Strict** .  
  
### <a name="conditions"></a>Aby ustawić konfiguracje ostrzeżeń w IDE  
 Gdy używasz [strony Kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) zamiast instrukcji `Option Strict`, masz dodatkową kontrolę nad warunkami, które generują błędy. Sekcja **konfiguracje ostrzeżeń** na **stronie kompilacja** zawiera ustawienia, które odpowiadają trzem warunkom, które powodują błąd w czasie kompilacji, gdy `Option Strict` jest włączona. Poniżej przedstawiono następujące ustawienia:  
  
- **Niejawna konwersja**  
  
- **Późne wiązanie; Wywołanie może zakończyć się niepowodzeniem w czasie wykonywania**  
  
- **Niejawny typ; przyjęto obiekt**  
  
 Jeśli ustawisz **opcję Strict** to **on**, wszystkie trzy z tych ustawień konfiguracyjnych ostrzeżeń mają ustawioną wartość **błąd**. Ustawienie **opcji Strict** to **off**powoduje, że wszystkie trzy ustawienia mają wartość **none**.  
  
 Można indywidualnie zmienić każde ustawienie konfiguracji ostrzegawczej na **none**, **Warning**lub **Error**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzegawczej są ustawione na **błąd**, `On` pojawia się w polu `Option strict`. Jeśli wszystkie trzy wartości są ustawione na **Brak**, w tym polu pojawia się `Off`. Dla każdej innej kombinacji tych ustawień pojawia się **(niestandardowe)** .  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Aby ustawić ustawienie opcji Stricted Default dla nowych projektów  
 Podczas tworzenia projektu ustawienie **opcji Strict** na karcie **kompilowania** jest ustawione na wartość ustawienia **Strict** w oknie dialogowym **Opcje** .  
  
 Aby ustawić `Option Strict` w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie w **języku VB** domyślnie jest `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Aby ustawić Option Strict w wierszu polecenia  
 Dołącz opcję kompilatora [/optionstrict —](../../../visual-basic/reference/command-line-compiler/optionstrict.md) do polecenia **VBC** .  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przedstawiono błędy czasu kompilowania spowodowane przez niejawne konwersje typów, które są zawężające konwersje. Ta kategoria błędów odpowiada warunkowi **niejawnej konwersji** na **stronie kompilowania**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje błąd czasu kompilacji spowodowany późnym wiązaniem. Ta kategoria błędów odnosi się do **późnego wiązania; wywołanie może zakończyć się niepowodzeniem w czasie wykonywania** na **stronie kompilacji**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przedstawiono błędy spowodowane przez zmienne, które są zadeklarowane przy użyciu niejawnego typu `Object`. Ta kategoria błędów odpowiada **typowi niejawnemu; obiekt przyjmuje** warunek na **stronie kompilowania**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Instrukcje: dostęp do elementów członkowskich obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Późne powiązania w rozwiązaniach pakietu Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
