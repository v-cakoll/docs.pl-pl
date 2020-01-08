---
title: 'Samouczek: Napisz pierwszy Analizator i poprawkę kodu'
description: Ten samouczek zawiera instrukcje krok po kroku dotyczące kompilowania analizatora i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (interfejsy API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 99401e74588088d56b3fbd916e050f5d468722a1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346939"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Samouczek: Napisz pierwszy Analizator i poprawkę kodu

Zestaw SDK .NET Compiler Platform zawiera narzędzia potrzebne do tworzenia niestandardowych ostrzeżeń, które są przeznaczone C# dla kodu lub Visual Basic. **Analizator** zawiera kod, który rozpoznaje naruszenia reguły. **Poprawka kodu** zawiera kod, który naprawia naruszenie. Implementowane reguły mogą być dowolne od struktury kodu do stylu kodowania do konwencji nazewnictwa i nie tylko. .NET Compiler Platform zapewnia strukturę do uruchamiania analizy, ponieważ deweloperzy piszą kod i wszystkie funkcje interfejsu użytkownika programu Visual Studio umożliwiające naprawianie kodu: wyświetlanie zygzaków w edytorze, zapełnianie Lista błędów programu Visual Studio, tworzenie "żarówki" sugestie i pokazujące zaawansowaną wersję zapoznawczą sugerowanych poprawek.

W tym samouczku przedstawiono tworzenie **analizatora** i dołączoną **poprawkę kodu** przy użyciu interfejsów API Roslyn. Analizator jest sposobem przeprowadzenia analizy kodu źródłowego i zgłoszenia problemu do użytkownika. Opcjonalnie Analizator może również dostarczyć poprawkę kodu, która reprezentuje modyfikację kodu źródłowego użytkownika. Ten samouczek tworzy Analizator, który wyszukuje deklaracje zmiennych lokalnych, które mogą być deklarowane przy użyciu modyfikatora `const`, ale nie są. Poprawka kodu towarzyszącego modyfikuje te deklaracje w celu dodania modyfikatora `const`.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

Musisz zainstalować **zestaw SDK .NET compiler platform** za pomocą Instalator programu Visual Studio:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Istnieje kilka kroków, które należy wykonać, aby utworzyć i zweryfikować analizator:

1. Utwórz rozwiązanie.
1. Zarejestruj nazwę i opis analizatora.
1. Ostrzeżenia i zalecenia analizatora raportów.
1. Zaimplementuj poprawkę kodu, aby akceptować zalecenia.
1. Popraw analizę poprzez testy jednostkowe.

## <a name="explore-the-analyzer-template"></a>Eksplorowanie szablonu analizatora

Analizator raportuje do użytkownika wszystkie deklaracje zmiennych lokalnych, które mogą być konwertowane na stałe lokalne. Rozważmy na przykład następujący kod:

```csharp
int x = 0;
Console.WriteLine(x);
```

W powyższym kodzie, `x` ma przypisaną stałą wartość i nigdy nie jest modyfikowana. Można go zadeklarować przy użyciu modyfikatora `const`:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Analiza umożliwiająca ustalenie, czy zmienna może być stałą, jest uwzględniana, wymagająca analizy składniowej, stałej analizie wyrażenia inicjatora i analizy przepływu danych, aby upewnić się, że zmienna nigdy nie jest zapisywana. .NET Compiler Platform udostępnia interfejsy API, które ułatwiają wykonywanie tej analizy. Pierwszym krokiem jest utworzenie nowej C# **analizatora z poprawkami kodu** Project.

- W programie Visual Studio wybierz kolejno pozycje **plik > nowy > projekt...** , aby wyświetlić okno dialogowe Nowy projekt.
- W **obszarze C# rozszerzalność Visual >** , wybierz opcję **Analizator z poprawkami kodu (.NET standard)** .
- Nadaj projektowi nazwę "**MakeConst**" i kliknij przycisk OK.

Analizator z szablonem poprawki kodu tworzy trzy projekty: jeden zawiera Analizator i poprawkę kodu, drugi jest projektem testu jednostkowego, a trzeci jest projektem VSIX. Domyślny projekt startowy jest projektem VSIX. Naciśnij klawisz **F5** , aby uruchomić projekt VSIX. Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, które załadowało nowy Analizator.

> [!TIP]
> Po uruchomieniu analizatora zostanie rozpoczęta druga kopia programu Visual Studio. Druga kopia używa innej gałęzi rejestru do przechowywania ustawień. Pozwala to na odróżnienie ustawień wizualizacji w dwóch kopiach programu Visual Studio. Możesz wybrać inny motyw dla eksperymentalnego przebiegu programu Visual Studio. Ponadto nie należy przeroamingować ustawień ani zalogować się do konta programu Visual Studio przy użyciu eksperymentalnego przebiegu programu Visual Studio. Te ustawienia są inne.

W drugim wystąpieniu programu Visual Studio, które właśnie zostało uruchomione, Utwórz nowy C# projekt aplikacji konsolowej (projekt .NET Core lub .NET Framework Project będzie działać — analizatory pracują na poziomie źródła). Umieść kursor nad tokenem podkreślonym linią falistą i pojawi się tekst ostrzegawczy podany przez analizator.

Szablon tworzy Analizator, który raportuje Ostrzeżenie dla każdej deklaracji typu, gdzie nazwa typu zawiera małe litery, jak pokazano na poniższym rysunku:

![Ostrzeżenie dotyczące raportowania analizatora](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Szablon zawiera również poprawkę kodu, która zmienia nazwę dowolnego typu zawierającego małe litery na wielkie litery. Możesz kliknąć ikonę żarówki wyświetlaną z ostrzeżeniem, aby zobaczyć sugerowane zmiany. Zaakceptowanie sugerowanych zmian aktualizuje nazwę typu i wszystkie odwołania do tego typu w rozwiązaniu. Teraz, gdy już widzisz początkową analizator w działaniu, Zamknij drugie wystąpienie programu Visual Studio i wróć do projektu analizatora.

Nie trzeba rozpoczynać drugiej kopii programu Visual Studio i utworzyć nowego kodu do testowania każdej zmiany w analizatorze. Szablon tworzy również projekt testu jednostkowego. Ten projekt zawiera dwa testy. `TestMethod1` pokazuje typowy format testu, który analizuje kod bez wyzwalania diagnostyki. `TestMethod2` pokazuje format testu, który wyzwala diagnostykę, a następnie stosuje sugerowaną poprawkę kodu. Podczas kompilowania analizatora i poprawki kodu należy napisać testy dla różnych struktur kodu w celu zweryfikowania pracy. Testy jednostkowe dla analizatorów są znacznie szybsze niż testowanie ich interaktywnie przy użyciu programu Visual Studio.

> [!TIP]
> Testy jednostkowe analizatora są doskonałym narzędziem, gdy wiesz, jakie konstrukcje kodu powinny być i nie powinny wyzwalać analizatora. Ładowanie analizatora w innej kopii programu Visual Studio to doskonałe narzędzie do eksplorowania i znajdowania konstrukcji, które nie zostały jeszcze przemyślane.

## <a name="create-analyzer-registrations"></a>Tworzenie rejestracji analizatora

Szablon tworzy początkową klasę `DiagnosticAnalyzer` w pliku **MakeConstAnalyzer.cs** . Ta początkowa Analizator przedstawia dwie ważne właściwości każdej analizatora.

- Każdy Analizator diagnostyki musi dostarczyć atrybut `[DiagnosticAnalyzer]`, który opisuje język, w którym działa.
- Każdy Analizator diagnostyki musi być pochodną klasy <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer>.

Szablon zawiera również podstawowe funkcje, które są częścią dowolnego analizatora:

1. Rejestrowanie akcji. Akcje reprezentują zmiany kodu, które powinny spowodować, że analizator sprawdzi kod pod kątem naruszeń. Gdy program Visual Studio wykrywa edycje kodu pasujące do zarejestrowanej akcji, wywołuje zarejestrowaną metodę analizatora.
1. Tworzenie diagnostyki. Po wykryciu naruszenia przez analizatora powstaje obiekt diagnostyczny używany przez program Visual Studio do powiadamiania użytkownika o naruszeniu.

Można rejestrować akcje w zastąpieniu metody <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType>. W tym samouczku zostaną odwiedzane **węzły składni** szukające lokalnych deklaracji i zobacz, które z nich mają stałe wartości. Jeśli deklaracja może być stała, Analizator utworzy i zgłosi diagnostykę.

Pierwszym krokiem jest zaktualizowanie stałych rejestracji i metody `Initialize`, aby te stałe wskazywały Analizator "Make const". Większość stałych ciągów jest zdefiniowana w pliku zasobów ciągu. Należy postępować zgodnie z tym rozwiązaniem, aby ułatwić lokalizację. Otwórz plik **resources. resx** dla projektu analizatora **MakeConst** . Spowoduje to wyświetlenie edytora zasobów. Zaktualizuj zasoby ciągu w następujący sposób:

- Zmień `AnalyzerTitle` na "zmienna może być stała".
- Zmień `AnalyzerMessageFormat` na "może to być stała".
- Zmień `AnalyzerDescription` na "Ustaw stałą".

Ponadto Zmień listę rozwijaną **modyfikator dostępu** na `public`. Ułatwia to korzystanie z tych stałych w testach jednostkowych. Po zakończeniu Edytor zasobów powinien wyglądać tak, jak pokazano na ilustracji:

![Aktualizowanie zasobów ciągów](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Pozostałe zmiany znajdują się w pliku analizatora. Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio. Zmień zarejestrowanej akcji z jednej, która działa w symbolach na jeden, który działa w składni. W metodzie `MakeConstAnalyzerAnalyzer.Initialize` Znajdź wiersz, który rejestruje akcję na symbole:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Zastąp go następującym wierszem:

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po tej zmianie można usunąć metodę `AnalyzeSymbol`. Ten Analizator bada <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, nie <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> instrukcji. Zwróć uwagę, że `AnalyzeNode` w tym kolorze czerwona. Właśnie dodany kod odwołuje się do metody `AnalyzeNode`, która nie została zadeklarowana. Zadeklaruj tę metodę przy użyciu następującego kodu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Zmień `Category` na "użycie" w **MakeConstAnalyzer.cs** , jak pokazano w poniższym kodzie:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Znajdowanie lokalnych deklaracji, które mogą być stałe

Czas zapisywania pierwszej wersji metody `AnalyzeNode`. Powinien on szukać pojedynczej deklaracji lokalnej, która może być `const` ale nie jest, podobnie jak w poniższym kodzie:

```csharp
int x = 0;
Console.WriteLine(x);
```

Pierwszym krokiem jest znalezienie lokalnych deklaracji. Dodaj następujący kod do `AnalyzeNode` w **MakeConstAnalyzer.cs**:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

To rzutowanie zawsze powiedzie się, ponieważ Analizator zarejestrował się pod kątem zmian lokalnych deklaracji i tylko deklaracji lokalnych. Żaden inny typ węzła nie wyzwala wywołania metody `AnalyzeNode`. Następnie sprawdź, czy w deklaracji zostały za`const` modyfikatory. Jeśli je znajdziesz, zwróć natychmiast. Poniższy kod szuka wszelkich modyfikatorów `const` w deklaracji lokalnej:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Na koniec należy sprawdzić, czy zmienna może być `const`. Oznacza to, że nigdy nie jest przypisywany po zainicjowaniu.

Przeprowadzasz analizę semantyki przy użyciu <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>. Użyj argumentu `context`, aby określić, czy można dokonać `const`deklaracji zmiennej lokalnej. <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym. Więcej informacji można znaleźć w artykule obejmującym [modele semantyczne](../work-with-semantics.md). Użyjesz <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> do przeprowadzenia analizy przepływu danych w lokalnej instrukcji deklaracji. Następnie użyj wyników tej analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywana z nową wartością w innym miejscu. Wywołaj metodę rozszerzenia <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A>, aby pobrać <xref:Microsoft.CodeAnalysis.ILocalSymbol> dla zmiennej i sprawdź, czy nie jest zawarta w kolekcji <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> analizy przepływu danych. Dodaj następujący kod na końcu metody `AnalyzeNode`:

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

Właśnie dodany kod gwarantuje, że zmienna nie jest modyfikowana i dlatego może zostać wprowadzona `const`. Czas na podniesienie poziomu diagnostyki. Dodaj następujący kod jako ostatni wiersz w `AnalyzeNode`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Możesz sprawdzić postęp, naciskając klawisz **F5** , aby uruchomić Analizator. Możesz załadować utworzoną wcześniej aplikację konsolową, a następnie dodać następujący kod testu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Powinna zostać wyświetlona Żarówka, a Analizator powinien zgłosić diagnostykę. Jednak żarówka nadal korzysta z wygenerowanej przez szablon poprawki kodu i informuje o tym, że można ją wielką literą. W następnej sekcji wyjaśniono, jak napisać poprawkę kodu.

## <a name="write-the-code-fix"></a>Napisz poprawkę kodu

Analizator może dostarczyć co najmniej jedną poprawkę kodu. Poprawka kodu definiuje edycję, która dotyczy zgłoszonego problemu. Dla utworzonej analizatora można podać poprawkę kodu, która wstawia słowo kluczowe const:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Użytkownik wybiera go z poziomu interfejsu użytkownika żarówki w edytorze, a program Visual Studio zmieni kod.

Otwórz plik **MakeConstCodeFixProvider.cs** dodany przez szablon.  Ta poprawka kodu jest już przewodowa do identyfikatora diagnostyki utworzonego przez analizatora diagnostycznego, ale nie implementuje jeszcze odpowiedniego przekształcenia kodu. Najpierw należy usunąć część kodu szablonu. Zmień ciąg tytułu na "Ustaw stałą":

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Następnie Usuń metodę `MakeUppercaseAsync`. Nie ma już zastosowania.

Wszyscy dostawcy poprawek kodu pochodzą z <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Wszystkie <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> przesłonięcia w celu zgłaszania poprawek kodu. W `RegisterCodeFixesAsync`Zmień typ węzła nadrzędnego, którego szukasz, na <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> w celu dopasowania do danych diagnostycznych:

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Następnie zmień ostatni wiersz, aby zarejestrować poprawkę kodu. Poprawka spowoduje utworzenie nowego dokumentu, który skutkuje dodaniem modyfikatora `const` do istniejącej deklaracji:

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Zobaczysz czerwone zygzaki w kodzie, który właśnie został dodany do symbolu `MakeConstAsync`. Dodaj deklarację dla `MakeConstAsync` jak w poniższym kodzie:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Nowa metoda `MakeConstAsync` przekształci <xref:Microsoft.CodeAnalysis.Document> reprezentujący plik źródłowy użytkownika do nowej <xref:Microsoft.CodeAnalysis.Document>, która zawiera teraz deklarację `const`.

Tworzysz nowy token `const` słowa kluczowego, aby wstawić go na początku instrukcji deklaracji. Należy zachować ostrożność, aby najpierw usunąć wszystkie wiodące kwizy z pierwszego tokenu instrukcji deklaracji i dołączyć je do tokenu `const`. Dodaj następujący kod do metody `MakeConstAsync`:

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Następnie Dodaj token `const` do deklaracji przy użyciu następującego kodu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Następnie sformatuj nową deklarację, aby dopasować C# reguły formatowania. Formatowanie zmian pod kątem zgodności z istniejącym kodem powoduje utworzenie lepszego środowiska. Dodaj następującą instrukcję bezpośrednio po istniejącym kodzie:

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Dla tego kodu jest wymagana Nowa przestrzeń nazw. Dodaj następującą instrukcję `using` na początku pliku:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Ostatnim krokiem jest dokonanie edycji. Ten proces obejmuje trzy kroki:

1. Pobierz uchwyt do istniejącego dokumentu.
1. Utwórz nowy dokument przez zastąpienie istniejącej deklaracji nową deklaracją.
1. Zwróć nowy dokument.

Dodaj następujący kod na końcu metody `MakeConstAsync`:

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Poprawka kodu jest gotowa do wypróbowania.  Naciśnij klawisz F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio. W drugim wystąpieniu programu Visual Studio Utwórz nowy C# projekt aplikacji konsolowej i Dodaj kilka lokalnych deklaracji zmiennych, które zostały zainicjowane z użyciem wartości stałych do metody Main. Zobaczysz, że są one raportowane jako ostrzeżenia poniżej.

![Może wprowadzać ostrzeżenia const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Wykonano wiele postępów. W deklaracji, które mogą zostać `const`. Jednak nadal działa. To działa prawidłowo, jeśli dodasz `const` do deklaracji zaczynających się od `i`, a następnie `j` i wreszcie `k`. Ale jeśli dodasz modyfikator `const` w innej kolejności, rozpoczynając od `k`, Analizator tworzy błędy: `k` nie można zadeklarować `const`, chyba że `i` i `j` są już `const`. W celu zapewnienia obsługi różnych zmiennych można zadeklarować i zainicjować więcej możliwości analizy.

## <a name="build-data-driven-tests"></a>Tworzenie testów opartych na danych

Analizator i poprawka kodu działają w prostym przypadku pojedynczej deklaracji, która może być poddana stałej. Istnieje wiele możliwych instrukcji deklaracji, w których ta implementacja wprowadza błędy. Te przypadki są rozwiązywane przez pracę z biblioteką testów jednostkowych zapisaną przez szablon. Jest to znacznie szybsze niż Wielokrotne otwieranie drugiej kopii programu Visual Studio.

Otwórz plik **MakeConstUnitTests.cs** w projekcie testów jednostkowych. Szablon utworzył dwa testy, które są zgodne z dwoma typowymi wzorcami w celu sprawdzenia, czy kod naprawi test jednostkowy. `TestMethod1` pokazuje wzorzec dla testu, który gwarantuje, że analizator nie zgłosi diagnostyki, gdy nie powinien. `TestMethod2` przedstawia wzorzec raportowania diagnostyki i uruchamiania poprawki kodu.

Kod prawie każdego testu dla analizatora jest zgodny z jednym z tych dwóch wzorców. W pierwszym kroku można wykonać te testy jako testy oparte na danych. Następnie można łatwo utworzyć nowe testy przez dodanie nowych stałych ciągów, aby reprezentować różne dane wejściowe testu.

W celu uzyskania skuteczności pierwszy krok polega na refaktoryzacji dwóch testów w testach opartych na danych. Następnie wystarczy zdefiniować tylko kilka ciągów stałych dla każdego nowego testu. Podczas refaktoryzacji Zmień nazwy obu tych metod na lepsze. Zastąp `TestMethod1` tym testem, który gwarantuje, że nie zostanie zgłoszona żadna Diagnostyka:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Można utworzyć nowy wiersz danych dla tego testu przez zdefiniowanie dowolnego fragmentu kodu, który nie powinien powodować wyzwalania ostrzeżenia przez diagnostykę. To Przeciążenie `VerifyCSharpDiagnostic` przebiega w przypadku braku wyzwalanej diagnostyki dla fragmentu kodu źródłowego.

Następnie zastąp `TestMethod2` tym testem, który zapewnia podniesienie poziomu diagnostyki i zastosowanie poprawki kodu do fragmentu kodu źródłowego:

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
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

Poprzedni kod również wprowadził kilka zmian w kodzie, który kompiluje oczekiwany wynik diagnostyki. Używa ona publicznych stałych zarejestrowanych w analizatorze `MakeConst`. Ponadto używa dwóch stałych ciągów dla źródła danych wejściowych i stałych. Dodaj następujące stałe ciągów do klasy `UnitTest`:

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Uruchom te dwa testy, aby upewnić się, że są one przekazywane. W programie Visual Studio Otwórz **Eksploratora testów** , wybierając kolejno pozycje **Test** > **Windows** > **Eksplorator testów**.  Naciśnij link **Uruchom wszystko** .

## <a name="create-tests-for-valid-declarations"></a>Utwórz testy dla prawidłowych deklaracji

Zgodnie z ogólną zasadą analizatory powinny zakończyć się tak szybko, jak to możliwe, wykonując minimalną pracę. Program Visual Studio wywołuje zarejestrowane analizatory, gdy użytkownik edytuje kod. Czas odpowiedzi jest wymaganym kluczem. Istnieje kilka przypadków testowych dla kodu, który nie powinien podnieść danych diagnostycznych. Analizator już obsługuje jeden z tych testów, przypadek, w którym zmienna jest przypisywana po zainicjowaniu. Dodaj następującą stałą ciągu do testów, aby reprezentować ten przypadek:

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Następnie Dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Ten test również kończy się powodzeniem. Następnie Dodaj stałe dla warunków, które nie zostały jeszcze obsłużone:

- Deklaracje, które są już `const`, ponieważ są już stałe:

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Deklaracje, które nie mają inicjatora, ponieważ nie ma wartości do użycia:

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Deklaracje, w których inicjator nie jest stałą, ponieważ nie mogą być stałymi czasu kompilacji:

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Może być jeszcze bardziej skomplikowany, C# ponieważ umożliwia stosowanie wielu deklaracji jako jednej instrukcji. Rozważmy następującą stałą ciągu przypadku testowego:

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Zmienna `i` może być stała, ale zmienna `j` nie może. W związku z tym nie można wykonać tej instrukcji jako deklaracji const. Dodaj deklaracje `DataRow` dla wszystkich tych testów:

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

Uruchom testy ponownie i zobaczysz, że te nowe przypadki testowe zakończą się niepowodzeniem.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Aktualizowanie analizatora w celu ignorowania prawidłowych deklaracji

Aby odfiltrować kod, który spełnia te warunki, potrzebne są pewne ulepszenia metody `AnalyzeNode` analizatora. Są to wszystkie powiązane warunki, więc podobne zmiany spowodują naprawienie wszystkich tych warunków. Wprowadź następujące zmiany w `AnalyzeNode`:

- Analiza semantyczna zbadała deklarację pojedynczej zmiennej. Ten kod musi znajdować się w pętli `foreach`, która bada wszystkie zmienne zadeklarowane w tej samej instrukcji.
- Każda zadeklarowana zmienna musi mieć inicjator.
- Każdy zadeklarowany inicjator zmiennej musi być stałą czasu kompilacji.

W metodzie `AnalyzeNode` Zastąp pierwotną analizę semantyczną:

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

z poniższym fragmentem kodu:

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

Pierwsza pętla `foreach` analizuje każdą deklarację zmiennej przy użyciu analizy składni. Pierwsze sprawdzenie gwarantuje, że zmienna ma inicjator. Druga kontrola gwarantuje, że inicjator jest stałą. Druga pętla ma pierwotną analizę semantyczną. Testy semantyczne znajdują się w osobnej pętli, ponieważ ma ona większy wpływ na wydajność. Uruchom testy ponownie, a wszystkie powinny być widoczne.

## <a name="add-the-final-polish"></a>Dodaj końcowy Polski

To już prawie koniec. Aby Analizator mógł obsłużyć kilka dodatkowych warunków. Program Visual Studio wywołuje analizatory podczas pisania kodu. Często zdarza się, że analizator zostanie wywołany dla kodu, który nie kompiluje. Metoda `AnalyzeNode` analizatora diagnostyki nie sprawdza, czy wartość stała jest możliwa do przekonwertowania na typ zmiennej. Dlatego bieżąca implementacja Happily konwersję niepoprawnej deklaracji, takiej jak int i = "ABC", na stałą lokalną. Dodaj stałą wartość ciągu źródłowego dla tego warunku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ponadto typy odwołań nie są prawidłowo obsługiwane. Jedyną wartością stałą dozwoloną dla typu referencyjnego jest `null`, z wyjątkiem tego, że <xref:System.String?displayProperty=nameWithType>, co umożliwia używanie literałów ciągów. Innymi słowy, `const string s = "abc"` jest dozwolony, ale `const object s = "abc"` nie jest. Ten fragment kodu weryfikuje ten warunek:

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Aby upewnić się, że musisz dodać kolejny test, aby mieć pewność, że można utworzyć deklarację stałą dla ciągu. Poniższy fragment kodu definiuje kod, który wywołuje diagnostykę, i kod po zastosowaniu poprawki:

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Na koniec Jeśli zmienna jest zadeklarowana za pomocą słowa kluczowego `var`, Poprawka kodu robi niewłaściwy element i generuje deklarację `const var`, która nie jest obsługiwana przez C# język. Aby naprawić ten błąd, Poprawka kodu musi zastąpić słowo kluczowe `var` nazwą wywnioskowanego typu:

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Te zmiany aktualizują deklaracje wiersza danych dla obu testów. Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersza danych:

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Na szczęście wszystkie powyższe usterki mogą być rozwiązywane przy użyciu tych samych metod, które zostały już zapamiętane.

Aby naprawić pierwszy błąd, najpierw Otwórz **DiagnosticAnalyzer.cs** i Znajdź pętlę Foreach, w której jest sprawdzana każda z inicjatorów deklaracji lokalnej, aby upewnić się, że są one przypisane do wartości stałych. Bezpośrednio _przed_ pierwszą pętlą foreach wywołaj `context.SemanticModel.GetTypeInfo()`, aby pobrać szczegółowe informacje o zadeklarowanym typie deklaracji lokalnej:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Następnie w pętli `foreach` Sprawdź każdy inicjator, aby upewnić się, że jest on konwertowany na typ zmiennej. Po upewnieniu się, że inicjator jest stałą, należy dodać następujące sprawdzenie:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Następna zmiana jest oparta na ostatnim. Przed zamykającym nawiasem klamrowym pierwszej pętli Foreach Dodaj następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciągiem lub wartością null.

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

Aby zamienić słowo kluczowe var na poprawną nazwę typu, należy napisać nieco więcej kodu w ramach dostawcy poprawek kodu. Wróć do **CodeFixProvider.cs**. Kod, który dodasz, wykonuje następujące czynności:

- Sprawdź, czy deklaracja jest deklaracją `var`, a jeśli jest:
- Utwórz nowy typ dla wnioskowanego typu.
- Upewnij się, że deklaracja typu nie jest aliasem. Jeśli tak, można zadeklarować `const var`.
- Upewnij się, że `var` nie jest nazwą typu w tym programie. (Jeśli tak, `const var` jest dozwolony).
- Uprość pełną nazwę typu

Dźwięki takie jak wiele kodu. Nie jest. Zastąp wiersz, który deklaruje i inicjuje `newLocal` przy użyciu następującego kodu. Następuje natychmiast po zainicjowaniu `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Musisz dodać jedną instrukcję `using`, aby użyć typu <xref:Microsoft.CodeAnalysis.Simplification.Simplifier>:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Uruchom testy i wszystkie powinny być przekazywane. Congratulate siebie, uruchamiając gotowy Analizator. Naciśnij kombinację klawiszy CTRL + F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio z załadowanym rozszerzeniem Roslyn Preview.

- W drugim wystąpieniu programu Visual Studio Utwórz nowy C# projekt aplikacji konsolowej i Dodaj `int x = "abc";` do metody Main. Z powodu pierwszej poprawki błędów nie należy podawać ostrzeżenia dla tej deklaracji zmiennej lokalnej (chociaż występuje błąd kompilatora w oczekiwany sposób).
- Następnie Dodaj `object s = "abc";` do metody Main. Ze względu na drugą poprawkę błędu nie należy podawać ostrzeżenia.
- Na koniec Dodaj kolejną zmienną lokalną, która używa słowa kluczowego `var`. Zobaczysz, że zostało zgłoszone ostrzeżenie i pojawi się sugestia poniżej lewej strony.
- Przenieś karetkę edytora na falistej podkreślenie i naciśnij klawisze CTRL +. Aby wyświetlić sugerowaną poprawkę kodu. Po wybraniu poprawki kodu należy zauważyć, że słowo kluczowe var jest teraz prawidłowo obsługiwane.

Na koniec Dodaj następujący kod:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po wprowadzeniu tych zmian otrzymujesz czerwoną literę tylko dla pierwszych dwóch zmiennych. Dodaj `const` do obu `i` i `j`i uzyskasz nowe ostrzeżenie na temat `k`, ponieważ teraz można `const`.

Gratulacje! Zostało utworzone pierwsze rozszerzenie .NET Compiler Platform, które wykonuje analizę kodu na bieżąco w celu wykrywania problemu i zawiera szybką poprawkę, aby rozwiązać ten problem. W ten sposób poznasz wiele interfejsów API kodu, które są częścią zestawu SDK .NET Compiler Platform (Roslyn interfejsy API). Możesz sprawdzić, czy pracujesz z [ukończonym przykładem](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w naszym repozytorium GitHub.

## <a name="other-resources"></a>Inne zasoby

- [Wprowadzenie do analizy składni](../get-started/syntax-analysis.md)
- [Wprowadzenie do analizy semantycznej](../get-started/semantic-analysis.md)
