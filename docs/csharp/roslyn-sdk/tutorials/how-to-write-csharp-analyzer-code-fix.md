---
title: 'Samouczek: Napisz swój pierwszy analizator i naprawić kod'
description: Ten samouczek zawiera instrukcje krok po kroku do tworzenia analizatora i poprawki kodu przy użyciu zestawu SDK kompilatora .NET (Roslyn API).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240553"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Samouczek: Napisz swój pierwszy analizator i naprawić kod

Zestaw SDK platformy kompilatora .NET udostępnia narzędzia potrzebne do tworzenia niestandardowych ostrzeżeń docelowych kodu C# lub Visual Basic. **Analizator** zawiera kod, który rozpoznaje naruszenia reguły. **Poprawka kodu** zawiera kod, który rozwiązuje naruszenie. Implementowane reguły mogą być doczdą się od struktury kodu do stylu kodowania do konwencji nazewnictwa i nie tylko. Platforma kompilatora .NET zapewnia platformę do uruchamiania analizy, ponieważ deweloperzy piszą kod, a wszystkie funkcje interfejsu użytkownika programu Visual Studio do naprawiania kodu: wyświetlanie squiggles w edytorze, wypełnianie listy błędów programu Visual Studio, tworzenie "żarówki" sugestie i pokazujący bogaty podgląd sugerowanych poprawek.

W tym samouczku przejrzysz tworzenie **analizatora** i towarzyszącej mu **poprawki kodu** przy użyciu interfejsów API Roslyn. Analizator jest sposobem na przeprowadzenie analizy kodu źródłowego i zgłoszenie problemu użytkownikowi. Opcjonalnie analizator może również podać poprawkę kodu, która reprezentuje modyfikację kodu źródłowego użytkownika. Ten samouczek tworzy analizator, który znajduje deklaracje zmiennych lokalnych, które mogą być zadeklarowane przy użyciu modyfikatora, `const` ale nie są. Załączony kod fix modyfikuje te deklaracje, `const` aby dodać modyfikator.

## <a name="prerequisites"></a>Wymagania wstępne

- [Studio wizualne 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

Musisz zainstalować zestaw **SDK platformy kompilatora .NET** za pośrednictwem Instalatora programu Visual Studio:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Istnieje kilka kroków do tworzenia i sprawdzania poprawności analizatora:

1. Utwórz rozwiązanie.
1. Zarejestruj nazwę i opis analizatora.
1. Zgłoś ostrzeżenia i zalecenia analizatora.
1. Zaimplementuj poprawkę kodu, aby zaakceptować zalecenia.
1. Usprawnij analizę za pomocą testów jednostkowych.

## <a name="explore-the-analyzer-template"></a>Poznaj szablon analizatora

Analizator raporty do użytkownika wszelkich deklaracji zmiennych lokalnych, które mogą być konwertowane na stałe lokalne. Rozważmy na przykład następujący kod:

```csharp
int x = 0;
Console.WriteLine(x);
```

W powyższym `x` kodzie jest przypisany wartość stała i nigdy nie jest modyfikowany. Można go zadeklarować `const` za pomocą modyfikatora:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Analiza w celu ustalenia, czy zmienna może być stała, wymaga analizy składniowej, stałej analizy wyrażenia inicjatora i analizy przepływu danych w celu zapewnienia, że zmienna nigdy nie jest zapisywana. Platforma kompilatora .NET udostępnia interfejsy API, które ułatwiają wykonywanie tej analizy. Pierwszym krokiem jest utworzenie nowego analizatora Języka C# **z projektem poprawki kodu.**

- W programie Visual Studio wybierz pozycję **Plik > Nowy > Project...** aby wyświetlić okno dialogowe Nowy projekt.
- W **obszarze Visual C# > rozszerzalność**wybierz pozycję **Analizator z poprawką kodu (.NET Standard).**
- Nazwij swój projekt "**MakeConst**" i kliknij przycisk OK.

Analizator z szablonem poprawki kodu tworzy trzy projekty: jeden zawiera analizator i poprawkę kodu, drugi jest projektem testu jednostkowego, a trzeci to projekt VSIX. Domyślnym projektem startowym jest projekt VSIX. Naciśnij **klawisz F5,** aby rozpocząć projekt VSIX. Spowoduje to uruchomienie drugiego wystąpienia programu Visual Studio, który załadował nowy analizator.

> [!TIP]
> Po uruchomieniu analizatora należy uruchomić drugą kopię programu Visual Studio. Ta druga kopia używa innej gałęzi rejestru do przechowywania ustawień. Umożliwia to odróżnienie ustawień wizualnych w dwóch kopiach programu Visual Studio. Możesz wybrać inny motyw eksperymentalnego przebiegu programu Visual Studio. Ponadto nie wędruj w ustawieniach ani nie loguj się do konta programu Visual Studio przy użyciu eksperymentalnego przebiegu programu Visual Studio. To sprawia, że ustawienia są różne.

W drugim wystąpieniu programu Visual Studio, które właśnie zostało uruchomione, utwórz nowy projekt aplikacji konsoli C# (projekt .NET Core lub .NET Framework będzie działać — analizatory działają na poziomie źródłowym). Umieść wskaźnik myszy na tokenie z falistym podkreśleniem, a zostanie wyświetlony tekst ostrzegawczy dostarczony przez analizator.

Szablon tworzy analizator, który zgłasza ostrzeżenie na każdej deklaracji typu, gdzie nazwa typu zawiera małe litery, jak pokazano na poniższym rysunku:

![Ostrzeżenie o raportowaniu analizatora](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Szablon zawiera również poprawkę kodu, która zmienia dowolną nazwę typu zawierającą małe litery na wszystkie wielkie litery. Możesz kliknąć na żarówkę wyświetlaną z ostrzeżeniem, aby zobaczyć sugerowane zmiany. Zaakceptowanie sugerowanych zmian aktualizuje nazwę typu i wszystkie odwołania do tego typu w rozwiązaniu. Teraz, gdy widzisz wstępnego analizatora w akcji, zamknij drugie wystąpienie programu Visual Studio i powrót do projektu analizatora.

Nie trzeba uruchomić drugą kopię programu Visual Studio i utworzyć nowy kod, aby przetestować każdą zmianę w analizatorze. Szablon tworzy również projekt testu jednostkowego dla Ciebie. Ten projekt zawiera dwa testy. `TestMethod1`pokazuje typowy format testu, który analizuje kod bez wyzwalania diagnostyki. `TestMethod2`pokazuje format testu, który wyzwala diagnostyki, a następnie stosuje sugerowaną poprawkę kodu. Podczas tworzenia analizatora i poprawki kodu, napiszesz testy dla różnych struktur kodu, aby zweryfikować swoją pracę. Testy jednostkowe analizatorów są znacznie szybsze niż testowanie ich interaktywnie za pomocą programu Visual Studio.

> [!TIP]
> Testy jednostkowe analizatora są doskonałym narzędziem, gdy wiesz, jakie konstrukcje kodu powinny i nie powinny wyzwalać analizatora. Ładowanie analizatora w innej kopii programu Visual Studio jest doskonałym narzędziem do eksplorowania i znajdowania konstrukcji, o których jeszcze nie myślałeś.

## <a name="create-analyzer-registrations"></a>Tworzenie rejestracji analizatora

Szablon tworzy klasę `DiagnosticAnalyzer` początkową w **pliku MakeConstAnalyzer.cs.** Ten wyjmator początkowy pokazuje dwie ważne właściwości każdego analizatora.

- Każdy analizator diagnostyczny musi zawierać atrybut opisujący `[DiagnosticAnalyzer]` język, na który działa.
- Każdy analizator diagnostyczny <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> musi pochodzić z klasy.

Szablon pokazuje również podstawowe funkcje, które są częścią dowolnego analizatora:

1. Rejestrowanie akcji. Akcje reprezentują zmiany kodu, które powinny wyzwolić analizator, aby zbadać kod pod kątem naruszeń. Gdy program Visual Studio wykryje zmiany kodu, które pasują do zarejestrowanej akcji, wywołuje zarejestrowaną metodę analizatora.
1. Tworzenie diagnostyki. Gdy analizator wykryje naruszenie, tworzy obiekt diagnostyczny, który używa programu Visual Studio do powiadamiania użytkownika o naruszeniu.

Rejestrujesz akcje w <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> zastąpiosz metodę. W tym samouczku odwiedzisz **węzły składni** w poszukiwaniu deklaracji lokalnych i zobaczysz, które z nich mają stałe wartości. Jeśli deklaracja może być stała, analizator utworzy i zgłosi diagnostykę.

Pierwszym krokiem jest zaktualizowanie stałych `Initialize` rejestracji i metody, dzięki czemu te stałe wskazują analizator "Make Const". Większość stałych ciągu są zdefiniowane w pliku zasobu ciągu. Należy postępować zgodnie z tą praktyką, aby ułatwić lokalizację. Otwórz plik **Resources.resx** dla projektu analizatora **MakeConst.** Spowoduje to wyświetlenie edytora zasobów. Zaktualizuj zasoby ciągu w następujący sposób:

- Zmień `AnalyzerTitle` na "Zmienna może być stała".
- Zmień `AnalyzerMessageFormat` na "Może być stała".
- Zmień `AnalyzerDescription` na "Make Constant".

Ponadto zmień **modyfikator dostępu** `public`rozwijanego do . Ułatwia to używanie tych stałych w testach jednostkowych. Po zakończeniu edytor zasobów powinien być wyświetlany na rysunku w następujący sposób:

![Aktualizowanie zasobów ciągu](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Pozostałe zmiany znajdują się w pliku analizatora. Otwórz **MakeConstAnalyzer.cs** w programie Visual Studio. Zmień zarejestrowaną akcję z akcji, która działa na symbole, na jedną, która działa na składnię. W `MakeConstAnalyzerAnalyzer.Initialize` metodzie znajdź wiersz, który rejestruje akcję na symbolach:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Zamień go na następujący wiersz:

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Po tej zmianie można `AnalyzeSymbol` usunąć metodę. Ten analizator <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>bada <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> , nie oświadczenia. Zauważ, `AnalyzeNode` że ma czerwone squiggles pod nim. Kod, który właśnie `AnalyzeNode` dodał, odwołuje się do metody, która nie została zadeklarowana. Deklaruj tę metodę przy użyciu następującego kodu:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Zmień `Category` na "Użycie" w **MakeConstAnalyzer.cs,** jak pokazano w poniższym kodzie:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Znajdź deklaracje lokalne, które mogą być const

Nadszedł czas, aby napisać pierwszą wersję `AnalyzeNode` metody. Należy szukać jednej deklaracji lokalnej, `const` która może być, ale nie jest, jak następujący kod:

```csharp
int x = 0;
Console.WriteLine(x);
```

Pierwszym krokiem jest znalezienie deklaracji lokalnych. Dodaj następujący kod `AnalyzeNode` do **MakeConstAnalyzer.cs:**

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Ta rzutowanie zawsze powiedzie się, ponieważ analizator zarejestrowany chwalenie dla zmian deklaracji lokalnych i tylko deklaracje lokalne. Żaden inny typ węzła wyzwala `AnalyzeNode` wywołanie metody. Następnie sprawdź deklarację dla `const` wszystkich modyfikatorów. Jeśli je znajdziesz, natychmiast wróć. Poniższy kod wyszbędzie żadnych `const` modyfikatorów deklaracji lokalnej:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Na koniec należy sprawdzić, czy `const`zmienna może być . Oznacza to upewnienie się, że nigdy nie jest przypisany po jego zainicjowaniu.

Wykonasz analizę semantyczną <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>za pomocą pliku . Argument służy `context` do określenia, czy można złożyć `const`deklarację zmiennej lokalnej . A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> reprezentuje wszystkie informacje semantyczne w jednym pliku źródłowym. Możesz dowiedzieć się więcej w artykule, który obejmuje [modele semantyczne](../work-with-semantics.md). Użyjesz <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> do wykonania analizy przepływu danych w instrukcji deklaracji lokalnej. Następnie należy użyć wyników tej analizy przepływu danych, aby upewnić się, że zmienna lokalna nie jest zapisywana z nową wartością nigdzie indziej. Wywołać <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> metodę rozszerzenia, <xref:Microsoft.CodeAnalysis.ILocalSymbol> aby pobrać dla zmiennej i sprawdzić, <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> czy nie jest zawarty z kolekcji analizy przepływu danych. Dodaj następujący kod na końcu `AnalyzeNode` metody:

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

Właśnie dodany kod zapewnia, że zmienna nie jest `const`modyfikowana i dlatego może być wykonana . Nadszedł czas, aby podnieść diagnostyki. Dodaj następujący kod jako ostatni `AnalyzeNode`wiersz w:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Możesz sprawdzić swoje postępy, naciskając **klawisz F5,** aby uruchomić analizator. Można załadować aplikację konsoli utworzoną wcześniej, a następnie dodać następujący kod testu:

```csharp
int x = 0;
Console.WriteLine(x);
```

Żarówka powinna pojawić się, a analizator powinien zgłosić diagnostykę. Jednak żarówka nadal używa szablonu wygenerowanego kodu naprawić i informuje, że może być wykonane wielkie litery. W następnej sekcji wyjaśniono, jak napisać poprawkę kodu.

## <a name="write-the-code-fix"></a>Napisz poprawkę kodu

Analizator może dostarczyć jedną lub więcej poprawek kodu. Poprawka kodu definiuje emisję, która rozwiązuje zgłoszony problem. Dla analizatora, który został utworzony, można podać poprawkę kodu, która wstawia const słowa kluczowego:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Użytkownik wybiera go z interfejsu użytkownika żarówki w edytorze i Visual Studio zmienia kod.

Otwórz plik **MakeConstCodeFixProvider.cs** dodany przez szablon.  Ta poprawka kodu jest już podłączona do identyfikatora diagnostycznego utworzonego przez analizator diagnostyczny, ale nie implementuje jeszcze przekształcenia odpowiedniego kodu. Najpierw należy usunąć niektóre z kodu szablonu. Zmień ciąg tytułu na "Make constant":

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Następnie usuń `MakeUppercaseAsync` metodę. To już nie ma zastosowania.

Wszyscy dostawcy poprawek kodu <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>pochodzą od . Wszystkie one <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> zastąpić do raportu dostępne poprawki kodu. W `RegisterCodeFixesAsync`przypadku zmiany typu węzła przodka, którego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> szukasz, na wartość diagnostyczną:

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Następnie zmień ostatni wiersz, aby zarejestrować poprawkę kodu. Poprawka utworzy nowy dokument, który `const` wynika z dodawania modyfikatora do istniejącej deklaracji:

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Zauważysz czerwone squiggles w kodzie, `MakeConstAsync`który właśnie dodał na symbolu . Dodaj deklarację `MakeConstAsync` dla podobnych, podobnych kodów:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Nowa `MakeConstAsync` metoda przekształci <xref:Microsoft.CodeAnalysis.Document> reprezentujący plik źródłowy użytkownika <xref:Microsoft.CodeAnalysis.Document> w nowy, `const` który teraz zawiera deklarację.

Utwórz nowy `const` token słów kluczowych, aby wstawić z przodu instrukcji deklaracji. Należy uważać, aby najpierw usunąć wszelkie wiodące ciekawostki z `const` pierwszego tokenu deklaracji instrukcji i dołączyć go do tokenu. Dodaj następujący kod do metody `MakeConstAsync`:

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Następnie dodaj `const` token do deklaracji przy użyciu następującego kodu:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Następnie sformatuj nową deklarację, aby dopasować reguły formatowania Języka C#. Formatowanie zmian w celu dopasowania istniejącego kodu zapewnia lepsze środowisko. Dodaj następującą instrukcję bezpośrednio po istniejącym kodzie:

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Dla tego kodu wymagany jest nowy obszar nazw. Dodaj następującą `using` instrukcję do górnej części pliku:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Ostatnim krokiem jest dokonanie edytowania. Istnieją trzy kroki tego procesu:

1. Uzyskaj uchwyt do istniejącego dokumentu.
1. Utwórz nowy dokument, zastępując istniejącą deklarację nową deklaracją.
1. Zwróć nowy dokument.

Dodaj następujący kod na końcu `MakeConstAsync` metody:

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Poprawka kodu jest gotowa do wypróbowania.  Naciśnij klawisz F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio. W drugim wystąpieniu programu Visual Studio utwórz nowy projekt aplikacji konsoli Języka C# i dodaj kilka deklaracji zmiennych lokalnych zainicjowanych z wartościami stałymi do Metody głównej. Zobaczysz, że są one zgłaszane jako ostrzeżenia, jak poniżej.

![Może tworzyć ostrzeżenia const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Zrobiłeś duży postęp. Istnieją squiggles pod deklaracjami, które `const`mogą być wykonane . Ale jest jeszcze wiele do zrobienia. To działa dobrze, `const` jeśli dodać do `i`deklaracji, począwszy od , następnie `j` i na koniec `k`. Ale jeśli dodasz `const` modyfikator w innej `k`kolejności, począwszy `k` od , analizator tworzy błędy: `const`nie można zadeklarować , `i` chyba że i `j` są już `const`. Musisz zrobić więcej analizy, aby upewnić się, że obsługuje różne sposoby zmienne mogą być deklarowane i inicjowane.

## <a name="build-data-driven-tests"></a>Tworzenie testów opartych na danych

Analizator i kod naprawić pracy na prostym przypadku pojedynczej deklaracji, które mogą być wykonane const. Istnieje wiele możliwych deklaracji oświadczenia, gdzie ta implementacja popełnia błędy. Te przypadki zostaną zaadresować, współpracując z biblioteką testów jednostkowych napisaną przez szablon. Jest znacznie szybszy niż wielokrotne otwieranie drugiej kopii programu Visual Studio.

Otwórz plik **MakeConstUnitTests.cs** w projekcie testu jednostkowego. Szablon utworzyli dwa testy, które są zgodne z dwoma typowymi wzorcami dla testu jednostkowego analizatora i kodu. `TestMethod1`pokazuje wzorzec dla testu, który zapewnia analizator nie zgłasza diagnostyki, gdy nie powinien. `TestMethod2`pokazuje wzorzec raportowania diagnostyki i uruchamiania poprawki kodu.

Kod dla prawie każdego testu analizatora następuje jeden z tych dwóch wzorców. W pierwszym kroku można przetworzyć te testy jako testy oparte na danych. Następnie będzie łatwo utworzyć nowe testy, dodając nowe stałe ciągu do reprezentowania różnych danych wejściowych testu.

Dla wydajności pierwszym krokiem jest refaktoryzacja dwóch testów do testów opartych na danych. Następnie należy zdefiniować tylko kilka stałych ciągu dla każdego nowego testu. Podczas refaktoryzacji, zmień nazwę obu metod na lepsze nazwy. Zamień `TestMethod1` na ten test, który zapewnia, że nie jest wywoływana żadna diagnostyka:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Można utworzyć nowy wiersz danych dla tego testu, definiując dowolny fragment kodu, który nie powinien powodować diagnostyki wyzwolić ostrzeżenie. To przeciążenie przebiegów, `VerifyCSharpDiagnostic` gdy nie ma diagnostyki wyzwalane dla fragmentu kodu źródłowego.

Następnie zastąp `TestMethod2` ten test, który zapewnia, że diagnostyka jest wywoływana i poprawka kodu zastosowana dla fragmentu kodu źródłowego:

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

Poprzedni kod również kilka zmian w kodzie, który tworzy oczekiwany wynik diagnostyczny. Używa stałych publicznych zarejestrowanych `MakeConst` w analizatorze. Ponadto używa dwóch stałych ciągu dla źródła wejściowego i stałego. Dodaj następujące stałe ciągu `UnitTest` do klasy:

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Uruchom te dwa testy, aby upewnić się, że przejdą. W programie Visual Studio otwórz **Eksploratora testów,** wybierając pozycję > **Eksplorator testów****systemu Windows** > . **Test**  Naciśnij łącze **Uruchom wszystko.**

## <a name="create-tests-for-valid-declarations"></a>Tworzenie testów dla prawidłowych deklaracji

Co do zasady analizatory powinny zakończyć pracę tak szybko, jak to możliwe, wykonując minimalną pracę. Visual Studio wywołuje zarejestrowane analizatory jako kod zmiany użytkownika. Czas reakcji jest kluczowym wymogiem. Istnieje kilka przypadków testowych dla kodu, który nie powinien podnieść diagnostyki. Analizator już obsługuje jeden z tych testów, w przypadku, gdy zmienna jest przypisana po zainicjowaniu. Dodaj następującą stałą ciągu do testów, aby reprezentować tę sprawę:

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Następnie dodaj wiersz danych dla tego testu, jak pokazano w poniższym fragmencie kodu:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Ten test również zaakkuje. Następnie dodaj stałe dla warunków, które jeszcze nie zostały obsłużonych:

- Deklaracje, które `const`są już , ponieważ są one już const:

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Deklaracje, które nie mają inicjatora, ponieważ nie ma żadnej wartości do użycia:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Deklaracje, w których inicjator nie jest stałą, ponieważ nie mogą być stałymi czaskompilacji:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

Może to być jeszcze bardziej skomplikowane, ponieważ C# umożliwia wiele deklaracji jako jedną instrukcję. Należy wziąć pod uwagę następujące stałej ciągu przypadku testowego:

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Zmienna `i` może być stała, `j` ale zmienna nie może. W związku z tym oświadczenie to nie może być deklaracją const. Dodaj `DataRow` deklaracje dla wszystkich tych testów:

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

Uruchom testy ponownie, a zobaczysz te nowe przypadki testowe nie powiedzie się.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Aktualizowanie analizatora w celu zignorowania poprawnych deklaracji

Potrzebujesz pewnych ulepszeń `AnalyzeNode` metody analizatora, aby odfiltrować kod, który pasuje do tych warunków. Są to wszystkie warunki pokrewne, więc podobne zmiany naprawią wszystkie te warunki. Wymiń `AnalyzeNode`następujące zmiany w :

- Analiza semantyczna zbadała pojedynczą deklarację zmiennej. Ten kod musi znajdować `foreach` się w pętli, która sprawdza wszystkie zmienne zadeklarowane w tej samej instrukcji.
- Każda zadeklarowana zmienna musi mieć inicjatora.
- Inicjator każdej zadeklarowanej zmiennej musi być stałą w czasie kompilacji.

W `AnalyzeNode` metodzie zastąp oryginalną analizę semantyczną:

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

z następującym fragmentem kodu:

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

Pierwsza `foreach` pętla sprawdza każdą deklarację zmiennej przy użyciu analizy składni. Pierwszy czek gwarantuje, że zmienna ma inicjatora. Drugi czek gwarantuje, że inicjator jest stałą. Druga pętla ma oryginalną analizę semantyczną. Kontrole semantyczne są w oddzielnej pętli, ponieważ ma większy wpływ na wydajność. Uruchom testy ponownie, a powinny zobaczyć je wszystkie przejść.

## <a name="add-the-final-polish"></a>Dodaj ostateczną polską

To już prawie koniec. Istnieje kilka innych warunków do obsługi analizatora. Visual Studio wywołuje analizatory, gdy użytkownik pisze kod. Często jest tak, że analizator zostanie wywołany dla kodu, który nie jest kompilowany. Metoda analizatora `AnalyzeNode` diagnostycznego nie sprawdza, czy wartość stała jest konwertowalna na typ zmiennej. Tak więc bieżąca implementacja będzie szczęśliwie konwertować niepoprawną deklarację, taką jak int i = "abc"' na stałą lokalną. Dodaj stałą ciągu źródłowego dla tego warunku:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ponadto typy odwołań nie są obsługiwane prawidłowo. Jedyną stałą wartością dozwoloną dla typu odwołania jest `null`, z wyjątkiem tego przypadku <xref:System.String?displayProperty=nameWithType>, co pozwala na literały ciągów. Innymi słowy, `const string s = "abc"` jest legalne, ale `const object s = "abc"` nie jest. Ten fragment kodu sprawdza ten warunek:

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Aby być dokładne, należy dodać kolejny test, aby upewnić się, że można utworzyć stałą deklarację dla ciągu. Poniższy fragment kodu definiuje zarówno kod, który podnosi diagnostyczne, jak i kod po zastosowaniu poprawki:

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Na koniec jeśli zmienna `var` jest zadeklarowana za pomocą słowa kluczowego, poprawka kodu wykonuje niewłaściwą `const var` rzecz i generuje deklarację, która nie jest obsługiwana przez język C#. Aby naprawić ten błąd, poprawka `var` kodu musi zastąpić słowo kluczowe nazwą wywnioskowanego typu:

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Te zmiany aktualizują deklaracje wierszy danych dla obu testów. Poniższy kod przedstawia te testy ze wszystkimi atrybutami wiersza danych:

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Na szczęście wszystkie powyższe błędy można rozwiązać przy użyciu tych samych technik, których właśnie się nauczyłeś.

Aby naprawić pierwszy błąd, najpierw otwórz **DiagnosticAnalyzer.cs** i zlokalizuj pętlę foreach, w której sprawdzane są każdego z inicjatorów deklaracji lokalnej, aby upewnić się, że są one przypisane ze stałymi wartościami. Bezpośrednio _przed_ pierwszą pętlą `context.SemanticModel.GetTypeInfo()` foreach wywołaj, aby pobrać szczegółowe informacje o zadeklarowanym typie deklaracji lokalnej:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Następnie w `foreach` pętli sprawdź każdy inicjator, aby upewnić się, że jest konwertowalny na typ zmiennej. Dodaj następujące sprawdzanie po upewnieniu się, że inicjator jest stałą:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Następna zmiana opiera się na ostatniej. Przed zamknięciem nawias klamrowy nawias u pierwszy foreach pętli, dodać następujący kod, aby sprawdzić typ deklaracji lokalnej, gdy stała jest ciąg lub null.

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

Musisz napisać nieco więcej kodu w dostawcy poprawki kodu, aby zastąpić var' słowo kluczowe z poprawną nazwą typu. Wróć do **CodeFixProvider.cs**. Kod, który dodasz, wykonuje następujące kroki:

- Sprawdź, czy deklaracja jest deklaracją `var` i czy jest:
- Utwórz nowy typ dla typu wywnioskowanego.
- Upewnij się, że deklaracja typu nie jest aliasem. Jeśli tak, to jest `const var`legalne, aby zadeklarować .
- Upewnij się, że `var` nie jest to nazwa typu w tym programie. (Jeśli tak, `const var` to jest legalne).
- Uprość pełną nazwę typu

To brzmi jak dużo kodu. Tak nie jest. Zamień wiersz, który deklaruje `newLocal` i inicjuje następującykod. Idzie natychmiast po inicjalizacji: `newModifiers`

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Aby użyć tego typu, należy dodać jedną `using` instrukcję: <xref:Microsoft.CodeAnalysis.Simplification.Simplifier>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Uruchom testy, a wszystkie powinny przejść. Pogratuluj sobie, uruchamiając gotowy analizator. Naciśnij klawisze Ctrl+F5, aby uruchomić projekt analizatora w drugim wystąpieniu programu Visual Studio z załadowanym rozszerzeniem Roslyn Preview.

- W drugim wystąpieniu programu Visual Studio utwórz nowy `int x = "abc";` projekt aplikacji konsoli Języka C# i dodaj do Metody głównej. Dzięki pierwszej poprawce błędu nie należy zgłaszać żadnego ostrzeżenia dla tej deklaracji zmiennej lokalnej (chociaż zgodnie z oczekiwaniami występuje błąd kompilatora).
- Następnie dodaj `object s = "abc";` do Main metody. Ze względu na drugą poprawkę błędu nie należy zgłaszać żadnego ostrzeżenia.
- Na koniec dodaj inną zmienną lokalną, która używa słowa kluczowego. `var` Zobaczysz, że ostrzeżenie jest zgłaszane, a pod po lewej stronie pojawi się sugestia.
- Przesuń opiekuna edytora nad falistą podkreśleniem i naciśnij klawisze Ctrl+. , aby wyświetlić sugerowaną poprawkę kodu. Po wybraniu poprawki kodu należy pamiętać, że słowo kluczowe var jest teraz obsługiwane poprawnie.

Na koniec dodaj następujący kod:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Po tych zmianach, masz czerwone squiggles tylko na pierwszych dwóch zmiennych. Dodaj `const` do `i` `j`obu i , i `k` pojawi się nowe `const`ostrzeżenie, ponieważ może być teraz .

Gratulacje! Utworzono pierwsze rozszerzenie platformy kompilatora .NET, które wykonuje analizę kodu w locie w celu wykrycia problemu i zapewnia szybką poprawkę, aby go poprawić. Po drodze nauczysz się wielu interfejsów API kodu, które są częścią sdk platformy kompilatora .NET (Roslyn Interfejsów API). Możesz sprawdzić swoją pracę na [ukończonym przykładzie](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) w naszym repozytorium GitHub.

## <a name="other-resources"></a>Inne zasoby

- [Wprowadzenie do analizy składni](../get-started/syntax-analysis.md)
- [Wprowadzenie do analizy semantycznej](../get-started/semantic-analysis.md)
