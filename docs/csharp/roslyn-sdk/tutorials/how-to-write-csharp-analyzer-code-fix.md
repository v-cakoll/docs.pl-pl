---
title: 'Samouczek: Pisanie Twojego pierwszego analizator i poprawkę kodu'
description: Ten samouczek zawiera instrukcje krok po kroku kompilacji analizator i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (interfejsy API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 2959fe3008bfca972d3a164ed27d05c2a8b0e69a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171754"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Samouczek: Pisanie Twojego pierwszego analizator i poprawkę kodu

Zestaw SDK platformy kompilatora .NET zapewnia narzędzia potrzebne do tworzenia niestandardowych ostrzeżenia tego docelowego języka C# lub kod języka Visual Basic. Twoje **analizatora** zawiera kod, który rozpoznaje naruszenia reguły. Twoje **poprawki kodu** zawiera kod, który poprawia naruszenie. Reguły, które można zaimplementować może być cokolwiek — od struktury kodu w celu kodowania styl do konwencji nazewnictwa i nie tylko. Platforma kompilatora .NET zapewnia platformę na uruchamianie analizy, programistom pisania kodu i naprawianie kodu funkcji wszystkich interfejsie użytkownika Visual Studio: wyświetlanie faliste linie w edytorze podczas wypełniania Visual Studio liście błędów, tworzenia "żarówka" sugestie i wyświetlanie podglądu sugerowanej poprawki.

W tym samouczku dowiesz się o tworzenie **analizatora** i towarzyszące **poprawki kodu** przy użyciu interfejsów API Roslyn. Analizator jest sposób wykonaj analizę kodu źródłowego i zgłosić problem do użytkownika. Opcjonalnie analizator oferuje również poprawki kodu, reprezentujący zmiany do kodu źródłowego użytkownika. Ten samouczek tworzy analizatora, który umożliwia znalezienie lokalnych deklaracji zmiennych, które mogą być deklarowane przy użyciu `const` modyfikator to. Towarzyszący poprawki kodu modyfikuje te deklaracje, aby dodać `const` modyfikator.

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio 2017](https://www.visualstudio.com/downloads)

Należy zainstalować **zestawu SDK platformy kompilatora .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Istnieje kilka kroków do tworzenia i weryfikowania Twojej analizatora:

1. Utwórz rozwiązanie.
1. Zarejestruj analizatora nazwę i opis.
1. Ostrzeżenia dotyczące analizatora raportu i zalecenia.
1. Implementowanie poprawki kodu, aby zaakceptować zalecenia.
1. Zwiększ analizy za pomocą testów jednostkowych.

## <a name="explore-the-analyzer-template"></a>Zapoznaj się z szablonu analizatora

Twoje analizatora raporty użytkownikowi lokalne deklaracje zmiennych, które mogą być konwertowane na lokalnym stałymi. Na przykład rozważmy następujący kod:

```csharp
int x = 0;
Console.WriteLine(x);
```

W powyższym kodzie `x` jest przypisywana wartość stała i nie jest nigdy modyfikowany. Mogą być deklarowane przy użyciu `const` modyfikator:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Analizy, aby ustalić, czy zmienna jest możliwe stałej jest zaangażowana wymagających analizy składni, wyrażenia inicjatora stałej analizy i analizy przepływu danych, aby upewnić się, że zmienna nigdy nie są zapisywane. Platforma kompilatora .NET zawiera interfejsy API, które ułatwiają wykonywanie tej analizy. Pierwszym krokiem jest utworzenie nowego języka C# **Analyzer przy użyciu poprawki kodu** projektu.

* W programie Visual Studio, wybierz **Plik > Nowy > Projekt...**  Aby wyświetlić okno dialogowe Nowy projekt.
* W obszarze **Visual C# > rozszerzalności**, wybierz **Analyzer przy użyciu poprawki kodu (.NET Standard)**.
* Nazwij swój projekt "**MakeConst**" i kliknij przycisk OK.

Analizator za pomocą szablonu poprawki kodu tworzy trzy projekty: jedna z nich zawiera analizator i poprawki kodu, druga jest projekt testów jednostkowych, a trzeci jest projekt VSIX. Domyślny projekt startowy jest projekt VSIX. Naciśnij klawisz **F5** można uruchomić projekt VSIX. Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, który został załadowany z nowego analizatora.

> [!TIP]
> Po uruchomieniu analizatora sieci, możesz uruchomić drugą kopię programu Visual Studio. Ta druga kopia używa gałęzi rejestru różnych do przechowywania ustawień. To pozwala odróżnić visual ustawienia w dwóch kopii programu Visual Studio. Możesz wybrać inny motyw eksperymentalne uruchomieniu programu Visual Studio. Ponadto nie są przenoszone ustawień lub zaloguj się do programu Visual Studio konta przy użyciu eksperymentalnym uruchamiania programu Visual Studio. Które utrzymuje ustawienia są różne.

W drugim wystąpieniu programu Visual Studio został uruchomiony Utwórz nowy projekt aplikacji Konsolowej C# (.NET Core lub .NET Framework projekt będzie praca — praca analizatory na poziomie źródła.) Umieść kursor nad token z linią falistą i pojawia się tekst ostrzeżenia, dostarczone przez analizatora.

Ten szablon tworzy analizatora, który zgłosi ostrzeżenie w każdej deklaracji typu, których nazwa typu zawiera małe litery, jak pokazano na poniższej ilustracji:

![Analizator raportowania ostrzeżenie](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Szablon zawiera także poprawki kodu, który zmienia wszelkie nazwy typu zawierającego małe litery na wielkie litery. Kliknięcie żarówki wyświetlane z ostrzeżeniem, aby wyświetlić sugerowane zmiany. Akceptuje aktualizacje sugerowane zmiany nazwy typu i wszystkie odwołania do tego typu w rozwiązaniu. Teraz, gdy wiesz początkowej analizator w działaniu, zamknij drugie wystąpienie programu Visual Studio i powrócić do projektu analizator.

Nie trzeba uruchomić drugą kopię programu Visual Studio i Utwórz nowy kod, aby przetestować każda zmiana w analizatorze usługi. Ten szablon tworzy również projekt testów jednostkowych dla Ciebie. Ten projekt zawiera dwie próby. `TestMethod1` przedstawia typowy format test, który analizuje kod bez powodowania diagnostyki. `TestMethod2` Pokazuje format test, który wyzwala Diagnostyka, a następnie stosuje poprawki sugerowane kodu. Podczas tworzenia usługi analizator i poprawki kodu, piszesz testy dla struktur inny kod, aby sprawdzić swoją pracę. Testy jednostkowe dla analizatory są znacznie szybciej niż w przypadku testowania ich interaktywnie przy użyciu programu Visual Studio.

> [!TIP]
> Analizatora testów jednostkowych są doskonałym narzędziem, gdy wiesz, jaki kod konstrukcje powinien i nie powinny wyzwalać swoje analizatora. Podczas ładowania analizatora użytkownika w innej kopii programu Visual Studio jest doskonałym narzędziem eksplorować i Znajdź konstrukcji, które mogą nie mieć wiesz jeszcze.

## <a name="create-analyzer-registrations"></a>Tworzenie analizatora rejestracji

Ten szablon tworzy wstępne `DiagnosticAnalyzer` klasy w **MakeConstAnalyzer.cs** pliku. Ta początkowa analizatora pokazuje dwie ważne właściwości każdego analizatora.

* Należy podać co analizatora diagnostycznego `[DiagnosticAnalyzer]` atrybut, który opisuje język działa na.
* Każdy analizatora diagnostycznego musi pochodzić od klasy <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> klasy.

Szablon zawiera również podstawowe funkcje, które są częścią dowolnego analizatora:

1. Rejestrowanie akcji. Działania reprezentują zmiany kodu, które powinny wyzwalać swoje analizator badanie kodu za naruszenia. Gdy program Visual Studio wykryje edycji kodu, zgodne zarejestrowanych akcji, wywołuje zarejestrowanej metody swoje analizatora.
1. Utwórz diagnostyki. Gdy Twoja analizatora wykryje naruszenie, tworzy diagnostycznych obiekt, który używa programu Visual Studio w celu powiadamia użytkownika o naruszenie.

Rejestrowanie akcji w zastąpienie metody <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> metody. W tym samouczku będziesz odwiedź **węzłów składni** szuka deklaracji lokalnego i zobaczyć, który z tych wartości stałych. Jeśli deklaracja może być stała, Twoje analizatora utworzysz i zgłaszać diagnostyki.

Pierwszym krokiem jest zaktualizowanie stałe rejestracji i `Initialize` metody, dzięki czemu te stałe wskazują swoje analizatora "Wprowadzić Const". Większość stałych ciągów są definiowane w pliku zasobów ciągu. Należy przestrzegać tej praktyki dla lokalizacji łatwiejsze. Otwórz **Resources.resx** plik **MakeConst** projektu analizator. Spowoduje to wyświetlenie edytora zasobów. Zaktualizuj zasoby w postaci ciągów w następujący sposób:

* Zmiana `AnalyzerTitle` "Zmiennej może być przeprowadzone stałej".
* Zmiana `AnalyzerMessageFormat` "Może być przeprowadzone stałej".
* Zmiana `AnalyzerDescription` się "stałe".

Ponadto zmienić **modyfikator dostępu** menu rozwijane `public`. Które ułatwia korzystanie z tych stałych w testach jednostkowych. Po zakończeniu, Edytor zasobów powinna być taka jak wykonaj ilustracji pokazano:

![Aktualizują zasoby z ciągów](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Pozostałe zmiany znajdują się w pliku analizatora. Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio. Zmień zarejestrowanych akcji z jednego, który działa na symboli na taki, który działa na składni. W `MakeConstAnalyzerAnalyzer.Initialize` metody Znajdź wiersz, który rejestruje działanie symboli:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Zastąp go następujący wiersz:

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po tej zmianie, można usunąć `AnalyzeSymbol` metody. Sprawdza, czy ten analizatora <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, a nie <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> instrukcji. Należy zauważyć, że `AnalyzeNode` ma czerwone faliste linie w nim. Kod został właśnie dodany odwołania `AnalyzeNode` metody, która nie została zadeklarowana. Należy zadeklarować tej metody, używając następującego kodu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Zmiana `Category` do "Obciążenie" w **MakeConstAnalyzer.cs** jak pokazano w poniższym kodzie:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Znajdź lokalne deklaracje, które może być wartością stałą

Nadszedł czas na zapis pierwszą wersję `AnalyzeNode` metody. Powinno to wyglądać dla jednej deklaracji lokalnej, która może być `const` , ale nie jest dostępna, podobnie do poniższego kodu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Pierwszym krokiem jest aby znaleźć lokalne deklaracje. Dodaj następujący kod do `AnalyzeNode` w **MakeConstAnalyzer.cs**:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

To rzutowanie zawsze powiedzie się, ponieważ Twoje analizatora zarejestrowane zmiany lokalne deklaracje i jedynie lokalne deklaracje. Żaden inny typ węzła wyzwala wywołanie usługi `AnalyzeNode` metody. Następnie sprawdź deklaracji pod kątem dowolnego `const` modyfikatorów. Jeśli okaże się ich, zwracać natychmiast. Poniższy kod wyszukuje dowolny `const` modyfikatorów na lokalnej deklaracji:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Na koniec należy sprawdzić, czy zmienna może być `const`. Oznacza to, że właściwe nigdy nie została przypisana po inicjalizacji.

Możesz wykonać niektóre przy użyciu analizy semantycznej <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>. Możesz użyć `context` argumentu, aby ustalić, czy mogą być tworzone deklaracji zmiennej lokalnej `const`. A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym. Dowiedz się więcej z tego artykułu, który obejmuje [modeli semantycznych](../work-with-semantics.md). Użyjesz <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> przeprowadzić analizę przepływu danych w instrukcji deklaracji lokalnej. Następnie przy użyciu wyniki analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywane z nową wartością miejscach. Wywołaj <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodę rozszerzenia, aby pobrać <xref:Microsoft.CodeAnalysis.ILocalSymbol> dla zmiennej i upewnij się, że nie jest zawarte <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> zbierania danych przepływ analizy. Dodaj następujący kod na końcu `AnalyzeNode` metody:

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Kod, właśnie został dodany zapewnia nie jest modyfikowana zmienna, a może być przeprowadzana `const`. Nadszedł czas, aby zgłosić diagnostyczne. Dodaj następujący kod w ostatnim wierszu w `AnalyzeNode`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Można sprawdzić postęp, naciskając klawisz **F5** do uruchamiania analizatora sieci. Możesz załadować aplikację konsolową, która została utworzona wcześniej, a następnie dodaj następujący kod testu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Żarówki, powinien zostać wyświetlony, a Twoje analizatora powinien wysyłać raporty diagnostyczne. Jednak żarówki nadal używa poprawki kodu wygenerowanego szablonu i informuje, że może on wielkimi literami. W następnej sekcji objaśniono sposób pisania poprawki kodu.

## <a name="write-the-code-fix"></a>Zapis poprawki kodu

Analizator może zapewnić jedną lub więcej poprawek kodu. Poprawki kodu definiuje edycji, odnoszący się do zgłoszonego problemu. Dla analizatora, który został utworzony można podać poprawki kodu, który wstawia const — słowo kluczowe:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Użytkownik wybiera z żarówki interfejsu użytkownika w edytorze i programu Visual Studio zmian kodu.

Otwórz **MakeConstCodeFixProvider.cs** pliku dodawane przez szablon.  Ta poprawka kodu jest już powiązaną Identyfikator diagnostyczny generowane przez użytkownika analizatora diagnostycznego, ale nie implementuje on jeszcze przekształcenie prawo kodu. Najpierw należy usunąć niektóre kod szablonu. Zmień ciąg tytułu "Marka stała":

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Następnie należy usunąć `MakeUppercaseAsync` metody. Nie ma już zastosowania.

Wszystkie poprawki kodu pochodzić od <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Zastępują one wszystkie <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> do zgłaszania poprawki dostępne kodu. W `RegisterCodeFixesAsync`, Zmień typ węzła nadrzędnego szukasz do <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> do dopasowania diagnostyczne:

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Następnie należy zmienić ostatni wiersz, aby zarejestrować poprawki kodu. Rozwiązanie problemu spowoduje utworzenie nowego dokumentu, który jest wynikiem dodawania `const` modyfikator do istniejącej deklaracji:  

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Można zauważyć czerwone faliste linie w kodzie, który właśnie został dodany na symbol `MakeConstAsync`. Dodaj deklarację dla `MakeConstAsync` jak poniższy kod:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Nowy `MakeConstAsync` przekształci metoda <xref:Microsoft.CodeAnalysis.Document> reprezentujący użytkownika pliku źródłowego do nowego <xref:Microsoft.CodeAnalysis.Document> że teraz zawiera `const` deklaracji.

Możesz utworzyć nową `const` — słowo kluczowe token wstawiony na początku instrukcji deklaracji. Uważaj najpierw usunąć wszystkie wiodące elementy towarzyszące składni z pierwszy token instrukcji deklaracji i dołączyć go do `const` tokenu. Dodaj następujący kod do `MakeConstAsync` metody:

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Następnie dodaj `const` tokenu z deklaracją przy użyciu następującego kodu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Następnie sformatuj nowe oświadczenie do dopasowania reguły formatowania języka C#. Formatowanie zmiany, aby dopasować istniejący kod tworzy lepsze środowisko. Dodaj następującą instrukcję, natychmiast po istniejącym kodzie:

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Nowy obszar nazw jest wymagana dla tego kodu. Dodaj następujący kod `using` instrukcji na górze pliku:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Ostatnim krokiem jest zapewnienie edycji. Istnieją trzy kroki, aby ten proces:

1. Uzyskaj dojście do istniejącego dokumentu.
1. Utwórz nowy dokument przez zastąpienie istniejącej deklaracji nowe oświadczenie.
1. Zwraca nowy dokument.

Dodaj następujący kod na końcu `MakeConstAsync` metody:

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Poprawkę kod jest gotowy do wypróbowania.  Naciśnij klawisz F5, aby uruchomić projekt analizator w drugim wystąpieniu programu Visual Studio. W drugim wystąpieniu programu Visual Studio Utwórz nowy projekt aplikacji Konsolowej C# i dodaj kilka deklaracji zmiennych lokalnych zainicjować przy użyciu stałych wartości do metody Main. Zobaczysz, że są one raportowane jako ostrzeżenia, tak jak pokazano poniżej.

![Można wprowadzić const ostrzeżenia](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Wprowadzono wiele postępu. Istnieją faliste linie w deklaracjach, które mogą być wykonane `const`. Jednak nadal zadania do wykonania. To działa prawidłowo, jeśli dodasz `const` do deklaracji, począwszy od `i`, następnie `j` a na koniec `k`. Jednak jeśli dodasz `const` modyfikator i inną kolejność, począwszy od `k`, Twoje analizatora tworzy błędy: `k` nie można zadeklarować `const`, chyba że `i` i `j` są już `const`. Masz w celu dalszej analizy w celu zapewnienia obsługi różnych sposobów zmienne mogą być deklarowane i inicjowane.

## <a name="build-data-driven-tests"></a>Tworzenie testów opartych na danych

Twoje analizator i kod napraw pracy w prostym przypadku jednej deklaracji, które mogą być wykonane const. Istnieje wiele instrukcje deklaracji możliwe, w którym tej implementacji sprawia, że błędy. Te przypadki zaspokoić poprzez współdziałanie z Biblioteka testów jednostkowych, które są zapisywane przez szablon. Jest znacznie szybszy niż wielokrotnie otwieranie drugą kopię programu Visual Studio.

Otwórz **MakeConstUnitTests.cs** pliku w projekcie testów jednostkowych. Szablon utworzony dwóch testów, które należy wykonać dwie typowe wzorce dla analizatora oraz test jednostkowy poprawki kodu. `TestMethod1` Pokazuje, że wzorzec dla testów, które gwarantuje, że analizator nie zgłaszaj diagnostyki, gdy nie należy go. `TestMethod2` przedstawia wzorzec do raportowania diagnostyki i uruchamiania poprawki kodu.

Kod dla niemal każdego testu, Twoje analizatora następuje jeden z tych dwóch wzorców. W pierwszym kroku możesz przerabiać te testy jako testów opartych na danych. Następnie będzie można łatwo utworzyć nowe testy, dodając nowe stałych ciągów do reprezentowania danych wejściowych z różnych testów.

W celu zwiększenia wydajności pierwszym krokiem jest Refaktoryzacja dwóch testów do testów opartych na danych. Następnie wystarczy zdefiniować kilka stałych ciągów dla każdego nowego testu. Podczas refaktoryzacji, Zmień nazwę obu metod lepszych nazw. Zastąp `TestMethod1` jest wywoływane z tym testem, które gwarantuje, że nie diagnostyczne:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Można utworzyć nowego wiersza danych dla tego testu, definiując dowolnego fragmentu kodu, które nie powinny powodować usługi diagnostyczne do wyzwalania ostrzeżenia. To przeciążenie `VerifyCSharpDiagnostic` zostają spełnione, gdy nie ma żadnych diagnostyki wyzwolone dla fragmentu kodu źródłowego.  

Następnie zastąp `TestMethod2` za pomocą tego testu, które gwarantuje, że Diagnostyka jest wywoływane i poprawki kodu, stosowane dla tego fragmentu kodu źródłowego:

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

Powyższy kod również kilka zmian do kodu, który kompiluje oczekiwane wyniki diagnostyki. Używa ona publiczne stałe zarejestrowane w `MakeConst` analizatora. Ponadto używa dwóch stałych ciągów dla źródła danych wejściowych i stały. Dodaj następujące stałe ciągu do `UnitTest` klasy:

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Te dwa testy, aby upewnić się, że przechodzą uruchamiać. W programie Visual Studio, otwórz **Eksplorator testów** , wybierając **testu** > **Windows** > **Eksplorator testów**.  Następnie naciśnij klawisz **Uruchom wszystkie** łącza.

## <a name="create-tests-for-valid-declarations"></a>Tworzenie testów dla deklaracji na prawidłową

Zgodnie z ogólną zasadą analizatory powinno powodować wyjście tak szybko, jak to możliwe, minimalnym nakładzie pracy. Visual Studio wywołania zarejestrowany analizatory jako kod zmiany użytkownika. Czas odpowiedzi jest decydujące znaczenie. Istnieje kilka przypadków testowych dla kodu, który nie powinna podnieść swoje diagnostyki. Analizator swoje już obsługuje jeden z tych testów, w przypadku, gdy zmienna jest przypisywana zostały już zainicjowane. Dodaj następującą stałą ciągu do testów do reprezentowania tego przypadku:

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Następnie dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Ten test zakończy się pomyślnie także. Następnie dodaj stałe do warunków, które nie są jeszcze obsługiwane:

* Deklaracje, które zostały już `const`, ponieważ są one już const:

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* Deklaracje, które mają żadnego inicjatora, ponieważ nie ma wartości do użycia:

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* Deklaracje, gdy inicjator nie jest stałą, ponieważ nie mogą być stałe w czasie kompilacji:

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Można go jeszcze bardziej skomplikowane, ponieważ C# umożliwia wielu deklaracjach jako jedną instrukcję. Należy wziąć pod uwagę następujące stała typu string przypadek testowy:

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Zmienna `i` zyski, stała, natomiast zmienna `j` nie. W związku z tym ta instrukcja nie można dokonać const deklaracji. Dodaj `DataRow` deklaracje dla tych testów:

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Uruchom testy ponownie, a zobaczysz te nowe przypadki testowe, który się nie powieść.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Zaktualizuj swoje analizatora do ignorowania poprawiania deklaracji

Musisz wprowadzić ulepszenia usługi analizatora `AnalyzeNode` metodę, aby odfiltrować kod, który pasuje do tych warunków. Są one wszystkie powiązane warunki, więc podobne zmiany naprawi wszystkie te warunki. Wprowadź następujące zmiany do `AnalyzeNode`:

* Usługi analizy semantycznej zbadane Pojedyncza deklaracja zmiennej. Ten kod musi być zapisana w `foreach` pętli, która sprawdza, czy wszystkie zmienne zadeklarowane w tej samej instrukcji.
* Każdy zadeklarowana zmienna musi mieć inicjatora.
* Inicjator każdej zadeklarowanej zmiennej musi być stałą czasu kompilacji.

W swojej `AnalyzeNode` metody zastąpić oryginalnej analizy semantycznej:

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

następującym fragmentem kodu:

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

Pierwszy `foreach` pętli sprawdza, czy każdy deklaracja zmiennej za pomocą analizy składni. Sprawdź najpierw gwarantuje, że zmienna ma inicjatora. Drugi wyboru gwarantuje, że inicjator jest stałą. Drugi pętli ma oryginalnej analizy semantycznej. Semantyczne kontroli znajdują się w oddzielnych pętli, ponieważ ma on większy wpływ na wydajność. Ponownie uruchom testy i powinny one przekazywania.

## <a name="add-the-final-polish"></a>Dodaj końcowego Polski

Prawie gotowe. Istnieje kilka więcej warunków dla Twojego analizatora do obsługi. Program Visual Studio wywołuje analizatory podczas pisania kodu przez użytkownika. Często jest przypadek, który będzie analizatora użytkownika o nazwie do kodu, który nie kompilacji. Analizatora diagnostycznego `AnalyzeNode` metoda nie sprawdza, czy wartość stała jest konwertowany na typ zmiennej. Tak, bieżąca implementacja parametru trafem korzysta przekonwertuje nieprawidłową deklarację, takie jak int i = "abc" ' ze stałą lokalnego. Dodaj stałą typu string źródła dla tego warunku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ponadto typy odwołań nie są obsługiwane poprawnie. Tylko stała wartość dozwolona jest typem referencyjnym `null`, z wyjątkiem w tym przypadku <xref:System.String?displayPropert=nameWIthType>, co umożliwia literały ciągów znaków. Innymi słowy `const string s = "abc"` jest dozwolony, ale `const object s = "abc"` nie jest. Ten fragment kodu sprawdza tego warunku:

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Aby zapewnić dokładne, należy dodać kolejny test, aby upewnić się, który można utworzyć w deklaracji stałej ciągu. Poniższy fragment kodu definiuje kod, który wywołuje diagnostyczne i kod, po zastosowaniu poprawki:

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Ponadto jeśli zmienna jest zadeklarowana za pomocą `var` — słowo kluczowe, nie nic złego poprawki kodu i generuje `const var` deklaracji, który nie jest obsługiwany przez język C#. Aby rozwiązać ten problem, należy zastąpić poprawki kodu `var` — słowo kluczowe o nazwie wnioskowany typ:

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Te zmiany, zaktualizuj deklaracji wiersza danych w obu. Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersz danych:

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Na szczęście wszystkie powyższe błędy można reagować, wykonując te same techniki, które właśnie zaprezentowano.

Aby naprawić błąd pierwszy, należy najpierw otworzyć **DiagnosticAnalyzer.cs** i Znajdź pętli foreach, gdzie każda inicjatory deklaracji lokalnej sprawdzany w celu zapewnienia, są przypisani za pomocą wartości stałych. Od razu _przed_ pierwszy pętli foreach, wywołanie `context.SemanicModel.GetTypeInfo()` można pobrać szczegółowe informacje na temat zadeklarowanym typem deklaracji lokalnej:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Następnie wewnątrz swojej `foreach` pętli, należy sprawdzić każdego inicjatora, aby upewnić się, jest konwertowany na typ zmiennej. Dodaj następujące wyboru po upewnieniu się, że inicjator jest stałą:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Następna zmiana opiera się na ostatni z nich. Przed zamykający nawias klamrowy pierwszej instrukcji foreach pętli, należy dodać następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciąg lub wartość null.

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

Należy napisać kod bardziej w dostawcą poprawki kodu, aby zastąpić var' — słowo kluczowe o nazwie poprawnego typu. Wróć do **CodeFixProvider.cs**. Kod, który dodasz wykonuje następujące czynności:

* Sprawdź, czy deklaracja jest `var` deklaracji, jeśli jest:
* Tworzenie nowego typu dla typu wywnioskowanego.
* Upewnij się, że Deklaracja typu nie jest aliasem. Jeśli tak, jest legalne, aby zadeklarować `const var`.
* Upewnij się, że `var` nie jest nazwą typu, w tym programie. (Jeśli tak, `const var` jest legalna).
* Uprość Pełna nazwa typu

Czy wygląda na to duże ilości kodu. Nie jest dostępne. Zastąp wiersz, który deklaruje i inicjuje `newLocal` następującym kodem. Przechodzi ona od razu po zainicjowaniu `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Musisz dodać jeden `using` instrukcję, aby użyć <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> typu:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Uruchom testy i one wszystkich przejść. Pogratulować samodzielnie, uruchamiając usługi Zakończono analizatora. Naciśnij klawisze Ctrl + F5, aby uruchomić projekt analizator w drugim wystąpieniu programu Visual Studio z rozszerzeniem Roslyn w wersji zapoznawczej załadowane.

* Drugie wystąpienie programu Visual Studio Utwórz nowy projekt aplikacji Konsolowej C# i dodawać `int x = "abc";` do metody Main. Dzięki rozłożeniu w pierwszym poprawki bez ostrzeżenia powinny być raportowane dla tej deklaracji zmiennej lokalnej (chociaż zgodnie z oczekiwaniami, występuje błąd kompilatora).
* Następnie dodaj `object s = "abc";` do metody Main. Ze względu na drugim naprawienie usterki bez ostrzeżenia powinny być raportowane.
* Na koniec należy dodać inny zmiennej lokalnej, która używa `var` — słowo kluczowe. Zobaczysz, że ostrzeżenie jest zgłaszane i jest wyświetlany pod po lewej stronie.
* Przesuń karetkę edytora za pośrednictwem falistą, a następnie naciśnij klawisze Ctrl +. Aby wyświetlić poprawki sugerowane kodu. Po wybraniu poprawkę kodu, należy pamiętać, że var' — słowo kluczowe jest teraz obsługiwana prawidłowo.

Na koniec Dodaj następujący kod:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po wprowadzeniu tych zmian możesz uzyskać czerwone symbole tylko na pierwszych dwóch zmiennych. Dodaj `const` zarówno `i` i `j`, i uzyskuj nowe ostrzeżenie na `k` ponieważ mogą być teraz `const`.

Gratulacje! Utworzono pierwszego rozszerzenia platformy kompilatora .NET wykonuje analizę kodu na bieżąco, aby wykryć problem i zapewnia szybkiej poprawki, aby go rozwiązać. Po drodze kiedy znasz już wiele interfejsów API, które są częścią zestawu SDK platformy kompilatora .NET (interfejsy API Roslyn) kod. Możesz sprawdzić swoją pracę, względem [ukończone przykładowe](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w repozytorium przykładów GitHub. Możesz też pobrać [pliku zip projektu ukończona](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)

## <a name="other-resources"></a>Inne zasoby

- [Rozpoczynanie pracy z usługą analiza składni](../get-started/syntax-analysis.md)
- [Rozpoczynanie pracy z usługą analiza semantyki](../get-started/semantic-analysis.md)
