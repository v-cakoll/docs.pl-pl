---
title: Option Strict — Instrukcja
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
ms.openlocfilehash: 9c86ae6be86591445dde3cc4e7bdd38aa4a7f0fa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404346"
---
# <a name="option-strict-statement"></a>Option Strict — Instrukcja
Ogranicza niejawne konwersje typów danych tylko w celu poszerzenia konwersji, nie zezwala na późne wiązanie i uniemożliwia niejawne wpisywanie w wyniku `Object` typu.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`On`|Opcjonalny. Włącza `Option Strict` Sprawdzanie.|  
|`Off`|Opcjonalny. Wyłącza `Option Strict` Sprawdzanie.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy `Option Strict On` lub `Option Strict` pojawia się w pliku, następujące warunki powodują błąd czasu kompilacji:  
  
- Niejawne konwersje zawężające  
  
- Późne wiązanie  
  
- Niejawne wpisanie, które powoduje wystąpienie `Object` typu  
  
> [!NOTE]
> W konfiguracjach ostrzeżeń, które można ustawić na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), istnieją trzy ustawienia odpowiadające trzem warunkom, które powodują błąd w czasie kompilacji. Informacje o sposobach korzystania z tych ustawień znajdują [się w sekcji Aby ustawić konfiguracje ostrzeżeń w środowisku IDE](option-strict-statement.md#conditions) w dalszej części tego tematu.  
  
 `Option Strict Off`Instrukcja wyłącza błąd i sprawdzanie ostrzeżenia dla wszystkich trzech warunków, nawet jeśli skojarzone ustawienia IDE określają, czy te błędy lub ostrzeżenia mają zostać włączone. `Option Strict On`Instrukcja włącza kontrolę błędów i ostrzeżeń dla wszystkich trzech warunków, nawet jeśli skojarzone ustawienia IDE określają, aby wyłączyć te błędy lub ostrzeżenia.  
  
 Jeśli jest używana, `Option Strict` instrukcja musi znajdować się przed innymi instrukcjami kodu w pliku.  
  
 Po ustawieniu `Option Strict` na `On` , Visual Basic sprawdza, czy typy danych są określone dla wszystkich elementów programistycznych. Typy danych można określić jawnie lub określić za pomocą wnioskowania typu lokalnego. Zaleca się określenie typów danych dla wszystkich elementów programistycznych, z następujących powodów:  
  
- Umożliwia obsługę technologii IntelliSense dla zmiennych i parametrów. Dzięki temu można zobaczyć swoje właściwości i innych członków podczas wpisywania kodu.  
  
- Umożliwia kompilatorowi wykonywanie kontroli typu. Sprawdzanie typu ułatwia znalezienie instrukcji, które mogą zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów konwersji typu. Identyfikuje także wywołania metod dla obiektów, które nie obsługują tych metod.  
  
- Przyspiesza wykonywanie kodu. Jedną z przyczyn tego problemu jest to, że jeśli nie określisz typu danych dla elementu programistycznego, kompilator Visual Basic przypisze ten `Object` Typ. Skompilowany kod może wymagać konwersji z powrotem między `Object` i innych typów danych, co zmniejsza wydajność.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Niejawne Zawężanie błędów konwersji  
 Niejawne Zawężanie błędów konwersji występuje, gdy istnieje niejawna konwersja typu danych, która jest konwersją zawęża.  
  
 Visual Basic można skonwertować wiele typów danych na inne typy danych. Utrata danych może wystąpić, gdy wartość jednego typu danych jest konwertowana na typ danych o mniejszej dokładności lub mniejszej pojemności. Błąd czasu wykonywania występuje, gdy taka konwersja nie powiedzie się. `Option Strict`zapewnia powiadomienie w czasie kompilacji tych konwersji zawężających, aby można je było uniknąć. Aby uzyskać więcej informacji, zobacz [konwersje niejawne i jawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) oraz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Konwersje, które mogą spowodować błędy, zawierają niejawne konwersje występujące w wyrażeniach. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [+ — Operator](../operators/addition-operator.md)  
  
- [Operator + =](../operators/addition-assignment-operator.md)  
  
- [\ — Operator (Visual Basic)](../operators/integer-division-operator.md)  
  
- [Operator/= (Visual Basic)](../operators/floating-point-division-assignment-operator.md)  
  
- [Char, typ danych](../data-types/char-data-type.md)  
  
 Podczas łączenia ciągów przy użyciu [operatora&](../operators/concatenation-operator.md)wszystkie konwersje do ciągów są uznawane za rozszerzające. W związku z tym konwersje nie generują niejawnego zawężanego błędu konwersji, nawet jeśli `Option Strict` jest włączony.  
  
 Gdy wywoływana jest metoda, która ma argument, który ma typ danych różny od odpowiedniego parametru, konwersja zawęża powoduje błąd czasu kompilacji, jeśli `Option Strict` jest on włączony. Można uniknąć błędów czasu kompilacji przy użyciu konwersji rozszerzającej lub jawnej konwersji.  
  
 Niejawne Zawężanie błędów konwersji jest pomijane w czasie kompilacji w przypadku konwersji z elementów w `For Each…Next` kolekcji do zmiennej kontroli pętli. Dzieje się tak nawet wtedy, gdy `Option Strict` jest on włączony. Aby uzyskać więcej informacji, zobacz sekcję "Konwersje wąskie" w [dla każdego... Next — instrukcja](for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Błędy późnego wiązania  
 Obiekt jest późnie powiązany, gdy jest przypisany do właściwości lub metody zmiennej, która jest zadeklarowana jako typu `Object` . Aby uzyskać więcej informacji, zobacz [wczesne i późne wiązanie](../../programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Niejawne błędy typu obiektu  
 Niejawne błędy typu obiektu występują, gdy odpowiedni typ nie może zostać wywnioskowany dla zadeklarowanej zmiennej, więc typ `Object` jest wywnioskowany. Dzieje się tak głównie w przypadku używania `Dim` instrukcji w celu deklarowania zmiennej bez użycia `As` klauzuli i `Option Infer` jest wyłączona. Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](option-infer-statement.md) i [Specyfikacja języka Visual Basic](../../reference/language-specification/index.md).  
  
 W przypadku parametrów metody `As` klauzula jest opcjonalna, jeśli `Option Strict` jest wyłączona. Jeśli jednak którykolwiek z parametrów używa `As` klauzuli, wszystkie muszą z niej korzystać. Jeśli `Option Strict` jest włączona, `As` klauzula jest wymagana dla każdej definicji parametru.  
  
 Jeśli deklarujesz zmienną bez użycia `As` klauzuli i ustawisz ją na `Nothing` , zmienna ma typ `Object` . W takim przypadku nie występuje błąd czasu kompilacji, gdy `Option Strict` jest on włączony i `Option Infer` jest włączony. Przykładem jest `Dim something = Nothing` .  
  
### <a name="default-data-types-and-values"></a>Domyślne typy danych i wartości  
 W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w [instrukcji Dim](dim-statement.md).  
  
|Określono typ danych?|Określono inicjator?|Przykład|Wynik|  
|---|---|---|---|  
|Nie|Nie|`Dim qty`|Jeśli `Option Strict` jest wyłączone (wartość domyślna), zmienna jest ustawiona na `Nothing` .<br /><br /> Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|  
|Nie|Yes|`Dim qty = 5`|Jeśli `Option Infer` jest włączone (wartość domyślna), zmienna Pobiera typ danych inicjatora. Zobacz [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączona, zmienna Pobiera typ danych `Object` .<br /><br /> Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.|  
|Yes|Nie|`Dim qty As Integer`|Zmienna jest inicjowana do wartości domyślnej dla typu danych. Aby uzyskać więcej informacji, zobacz [Dim Statement](dim-statement.md).|  
|Tak|Tak|`Dim qty  As Integer = 5`|Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Gdy nie ma instrukcji Option Strict  
 Jeśli kod źródłowy nie zawiera `Option Strict` instrukcji, zostanie użyta **opcja ustawienie Strict** na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . **Strona kompilacja** zawiera ustawienia, które zapewniają dodatkową kontrolę nad warunkami, które generują błąd.  
  
 Jeśli używasz kompilatora wiersza polecenia, możesz użyć opcji kompilatora [-optionstrict](../../reference/command-line-compiler/optionstrict.md) , aby określić ustawienie dla `Option Strict` .  
  
### <a name="to-set-option-strict-in-the-ide"></a>Aby ustawić ustawienie Option Strict w środowisku IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. W **Eksplorator rozwiązań**wybierz projekt. W menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Na karcie **Kompilowanie** ustaw wartość w polu **Option Strict** .  
  
### <a name="to-set-warning-configurations-in-the-ide"></a><a name="conditions"></a>Aby ustawić konfiguracje ostrzeżeń w IDE  
 Gdy używasz [strony Kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) zamiast `Option Strict` instrukcji, masz dodatkową kontrolę nad warunkami, które generują błędy. Sekcja **konfiguracje ostrzeżeń** **strony kompilowania** zawiera ustawienia, które odpowiadają trzem warunkom, które powodują wystąpienie błędu kompilacji, gdy `Option Strict` jest włączony. Poniżej przedstawiono następujące ustawienia:  
  
- **Niejawna konwersja**  
  
- **Późne wiązanie; Wywołanie może zakończyć się niepowodzeniem w czasie wykonywania**  
  
- **Niejawny typ; przyjęto obiekt**  
  
 Jeśli ustawisz **opcję Strict** to **on**, wszystkie trzy z tych ustawień konfiguracyjnych ostrzeżeń mają ustawioną wartość **błąd**. Ustawienie **opcji Strict** to **off**powoduje, że wszystkie trzy ustawienia mają wartość **none**.  
  
 Można indywidualnie zmienić każde ustawienie konfiguracji ostrzegawczej na **none**, **Warning**lub **Error**. Jeśli wszystkie trzy ustawienia konfiguracji ostrzeżeń mają ustawioną wartość **błąd**, `On` pojawi się w `Option strict` polu. Jeśli wszystkie trzy z nich są ustawione na **Brak**, `Off` pojawia się w tym polu. Dla każdej innej kombinacji tych ustawień pojawia się **(niestandardowe)** .  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Aby ustawić ustawienie opcji Stricted Default dla nowych projektów  
 Podczas tworzenia projektu ustawienie **opcji Strict** na karcie **kompilowania** jest ustawione na wartość ustawienia **Strict** w oknie dialogowym **Opcje** .  
  
 Aby ustawić `Option Strict` w tym oknie dialogowym, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**. Początkowe domyślne ustawienie w **języku VB** domyślnie ma wartość `Off` .  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Aby ustawić Option Strict w wierszu polecenia  
 Dołącz opcję kompilatora [-optionstrict](../../reference/command-line-compiler/optionstrict.md) w poleceniu **VBC** .  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przedstawiono błędy czasu kompilowania spowodowane przez niejawne konwersje typów, które są zawężające konwersje. Ta kategoria błędów odpowiada warunkowi **niejawnej konwersji** na **stronie kompilowania**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje błąd czasu kompilacji spowodowany późnym wiązaniem. Ta kategoria błędów odnosi się do **późnego wiązania; wywołanie może zakończyć się niepowodzeniem w czasie wykonywania** na **stronie kompilacji**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przedstawiono błędy spowodowane przez zmienne, które są zadeklarowane z niejawnym typem `Object` . Ta kategoria błędów odpowiada **typowi niejawnemu; obiekt przyjmuje** warunek na **stronie kompilowania**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit, instrukcja](option-explicit-statement.md)
- [Funkcje konwersji typu](../functions/type-conversion-functions.md)
- [Porady: dostęp do elementów członkowskich obiektu](../../programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Wyrażenia osadzone w XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Swobodna konwersja delegatów](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Późne wiązania w rozwiązaniach pakietu Office](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
