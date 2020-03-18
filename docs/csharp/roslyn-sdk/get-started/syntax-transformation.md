---
title: Wprowadzenie do transformacji składni (interfejsy API Roslyn)
description: Wprowadzenie do przechodzenia, wykonywania zapytań i przechodzenia drzew składni.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5045dca839daba1070b34720e72cc9c4f7b94828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240613"
---
# <a name="get-started-with-syntax-transformation"></a>Wprowadzenie do transformacji składni

Ten samouczek opiera się na pojęciach i technikach eksplorowanych w [temacie Rozpocznij analizę składni](syntax-analysis.md) i rozpocznij pracę z przewodnikiem Szybki start [analizy semantycznej.](semantic-analysis.md) Jeśli jeszcze tego nie zrobiłeś, należy ukończyć te szybkie uruchamianie przed rozpoczęciem tego.

W tym przewodniku Szybki start można eksplorować techniki tworzenia i przekształcania drzew składni. W połączeniu z technikami, których nauczyłeś się w poprzednich przewodnikach Szybki start, tworzysz swoją pierwszą refaktoryzacją wiersza polecenia!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Niezmienność i platforma kompilatora .NET

**Niezmienność** jest podstawową zasadą platformy kompilatora .NET. Niezmienne struktury danych nie można zmienić po ich utworzeniu. Niezmienne struktury danych mogą być bezpiecznie udostępniane i analizowane przez wielu konsumentów jednocześnie. Nie ma niebezpieczeństwa, że jeden konsument wpływa na drugiego w nieprzewidywalny sposób. Analizator nie wymaga blokad lub innych środków współbieżności. Ta reguła ma zastosowanie do drzew składni, kompilacji, symboli, modeli semantycznych i każdej innej napotkanej struktury danych. Zamiast modyfikować istniejące struktury, interfejsy API tworzą nowe obiekty na podstawie określonych różnic w stosunku do starych. Ta koncepcja jest stosowana do drzew składni, aby utworzyć nowe drzewa przy użyciu przekształceń.

## <a name="create-and-transform-trees"></a>Tworzenie i przekształcanie drzew

Wybierz jedną z dwóch strategii dla przekształceń składni. **Metody fabryczne** są najlepiej używane podczas wyszukiwania określonych węzłów do zastąpienia lub określonych lokalizacji, w których chcesz wstawić nowy kod. **Ponowne moduły zapisujące** są najlepsze, gdy chcesz zeskanować cały projekt w poszukiwaniu wzorców kodu, które chcesz zastąpić.

### <a name="create-nodes-with-factory-methods"></a>Tworzenie węzłów z metodami fabrycznymi

Pierwsza transformacja składni demonstruje metody fabryczne. Zamierzasz zastąpić oświadczenie `using System.Collections;` `using System.Collections.Generic;` oświadczeniem. W tym przykładzie pokazano, jak tworzyć <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> obiekty przy użyciu metod <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> fabrycznych. Dla każdego rodzaju **węzła**, **tokenu**lub **ciekawostki** istnieje metoda fabryczna, która tworzy wystąpienie tego typu. Drzewa składni można tworzyć, redagując węzły hierarchicznie w sposób oddolny. Następnie przekształcisz istniejący program zastępując istniejące węzły nowym utworzonym drzewem.

Uruchom program Visual Studio i utwórz nowy projekt narzędzia do **analizy kodu autonomicznego** języka C#. W programie Visual Studio wybierz pozycję **Plik** > **nowy** > **projekt,** aby wyświetlić okno dialogowe Nowy projekt. W obszarze**Rozszerzalność** **języka Visual C#** > wybierz **autonomiczne narzędzie do analizy kodu**. Ten szybki start ma dwa przykładowe projekty, więc nazwij rozwiązanie **SyntaxTransformationQuickStart**i nazwij projekt **ConstructionCS**. Kliknij przycisk **OK**.

Ten projekt <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> używa metod klasy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> do konstruowania reprezentujących `System.Collections.Generic` obszar nazw.

Dodaj następujące za pomocą dyrektywy `Program.cs` do góry pliku, aby <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> zaimportować metody <xref:System.Console> fabryki klasy i metody, dzięki czemu można ich używać później bez ich kwalifikowania:

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Utworzysz **węzły składni nazw,** aby utworzyć `using System.Collections.Generic;` drzewo reprezentujące instrukcję. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>jest klasą podstawową dla czterech typów nazw, które pojawiają się w języku C#. Skomponuj te cztery typy nazw razem, aby utworzyć dowolną nazwę, która może pojawić się w języku C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, który reprezentuje proste nazwy `System` pojedynczego identyfikatora, takie jak i `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, który reprezentuje typ ogólny lub `List<int>`nazwę metody, taką jak .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, która reprezentuje kwalifikowaną nazwę `<left-name>.<right-identifier-or-generic-name>` formularza, `System.IO`taką jak .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, który reprezentuje nazwę przy użyciu złożenia extern alias taki . `LibraryV2::Foo`

<xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> Metoda służy do tworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> węzła. Dodaj następujący kod `Main` w `Program.cs`metodzie w:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Poprzedni kod tworzy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> obiekt i przypisuje go `name`do zmiennej . Wiele interfejsów API Roslyn zwraca klasy podstawowe, aby ułatwić pracę z powiązanymi typami. Zmienna `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>a , może być <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>ponownie użyty podczas tworzenia . Nie należy używać wnioskowania o typie podczas tworzenia próbki. Zautomatyzujesz ten krok w tym projekcie.

Nazwa została utworzona. Teraz nadszedł czas, aby zbudować więcej węzłów <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>w drzewie, budując . Nowe drzewo `name` używa jako lewej nazwy i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nowego `Collections` obszaru nazw jako prawej <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>strony . Dodaj następujący kod do pliku `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Uruchom kod ponownie i zobacz wyniki. Budujesz drzewo węzłów, które reprezentuje kod. Będziesz kontynuować ten wzorzec, aby utworzyć <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> dla obszaru `System.Collections.Generic`nazw . Dodaj następujący kod do pliku `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Uruchom program ponownie, aby zobaczyć, że masz skompilować drzewo dla kodu do dodania.

### <a name="create-a-modified-tree"></a>Tworzenie zmodyfikowanego drzewa

Zbudowano małe drzewo składni, które zawiera jedną instrukcję. Interfejsy API do tworzenia nowych węzłów są właściwym wyborem do tworzenia pojedynczych instrukcji lub innych małych bloków kodu. Jednak aby utworzyć większe bloki kodu, należy użyć metod, które zastępują węzły lub wstawić węzły do istniejącego drzewa. Pamiętaj, że drzewa składni są niezmienne. **Interfejs API składni** nie zapewnia żadnego mechanizmu modyfikowania istniejącego drzewa składni po zakończeniu budowy. Zamiast tego zapewnia metody, które produkują nowe drzewa na podstawie zmian do istniejących. `With*`metody są zdefiniowane w konkretnych klas, <xref:Microsoft.CodeAnalysis.SyntaxNode> które pochodzą z lub <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> w metod rozszerzenia zadeklarowanych w klasie. Metody te tworzą nowy węzeł, stosując zmiany do istniejących właściwości podrzędnych węzła. Ponadto metoda <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> rozszerzenia może służyć do zastąpienia węzła malejąco w poddrzewie. Ta metoda aktualizuje również element nadrzędny, aby wskazać nowo utworzonego elementu podrzędnego i powtarza ten proces w górę całego drzewa - proces znany jako _ponowne obracanie_ drzewa.

Następnym krokiem jest utworzenie drzewa, które reprezentuje cały (mały) program, a następnie zmodyfikować go. Dodaj następujący kod na początku `Program` klasy:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Przykładowy kod `System.Collections` używa obszaru nazw, a `System.Collections.Generic` nie obszaru nazw.

Następnie dodaj następujący kod do dolnej części `Main` metody, aby przeanalizować tekst i utworzyć drzewo:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

W tym <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> przykładzie użyto metody, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> aby zastąpić nazwę w węźle z jednym skonstruowane w poprzednim kodzie.

Utwórz <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> nowy węzeł <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> przy użyciu `System.Collections` metody, aby zaktualizować nazwę o nazwę utworzoną w poprzednim kodzie. Dodaj następujący kod do dolnej części `Main` metody:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Uruchom program i przyjrzyj się uważnie wyjściu. Nie `newusing` został umieszczony w drzewie głównym. Oryginalne drzewo nie zostało zmienione.

Dodaj następujący kod <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> przy użyciu metody rozszerzenia, aby utworzyć nowe drzewo. Nowe drzewo jest wynikiem zastąpienia istniejącego importu zaktualizowanym `newUsing` węzłem. To nowe drzewo można przypisać `root` do istniejącej zmiennej:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Uruchom program ponownie. Tym razem drzewo poprawnie importuje `System.Collections.Generic` obszar nazw.

### <a name="transform-trees-using-syntaxrewriters"></a>Przekształcanie drzew za pomocą`SyntaxRewriters`

Metody `With*` <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> i zapewniają wygodne środki do przekształcania poszczególnych gałęzi drzewa składni. Klasa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> wykonuje wiele przekształceń w drzewie składni. Klasa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> jest podklasą <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. Stosuje <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> transformację do określonego typu <xref:Microsoft.CodeAnalysis.SyntaxNode>. Przekształcenia można stosować do wielu <xref:Microsoft.CodeAnalysis.SyntaxNode> typów obiektów wszędzie tam, gdzie pojawiają się w drzewie składni. Drugi projekt w tym przewodniku Szybki start tworzy refaktoryzacji wiersza polecenia, który usuwa jawne typy w deklaracjach zmiennych lokalnych w dowolnym miejscu, że wnioskowanie typu może być używany.

Utwórz nowy projekt narzędzia do **analizy kodu autonomicznego** języka C#. W programie Visual Studio `SyntaxTransformationQuickStart` kliknij prawym przyciskiem myszy węzeł rozwiązania. Wybierz **pozycję Dodaj** > **nowy projekt,** aby wyświetlić okno **dialogowe Nowy projekt**. W obszarze**Rozszerzalność** **języka Visual C#** > wybierz pozycję **Autonomiczne narzędzie do analizy kodu**. Nazwij `TransformationCS` projekt i kliknij przycisk OK.

Pierwszym krokiem jest utworzenie klasy, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> która pochodzi z do wykonywania przekształceń. Dodaj nowy plik klasy do projektu. W programie Visual Studio wybierz pozycję **Project** > **Add Class...**. W **Add New Item** oknie `TypeInferenceRewriter.cs` dialogowym Dodawanie nowego elementu jako nazwa pliku.

Dodaj następujące dyrektywy do `TypeInferenceRewriter.cs` pliku:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Następnie upewnij `TypeInferenceRewriter` się, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> że klasa rozszerza klasę:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Dodaj następujący kod, aby zadeklarować prywatne pole <xref:Microsoft.CodeAnalysis.SemanticModel> tylko do odczytu, aby pomieścić i zainicjować je w konstruktorze. To pole będzie potrzebne później, aby określić, gdzie można użyć wnioskowania o typie:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Zastąp <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metodę:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Wiele interfejsów API Roslyn zadeklarować zwracać typy, które są klasami podstawowymi rzeczywistych typów czasu wykonywania zwracanych. W wielu scenariuszach jeden rodzaj węzła może zostać całkowicie zastąpiony przez inny rodzaj węzła lub nawet usunięty. W tym przykładzie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda <xref:Microsoft.CodeAnalysis.SyntaxNode>zwraca , zamiast pochodnego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>typu . To przepisanie <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> zwraca nowy węzeł na podstawie istniejącego.

Ten szybki start obsługuje deklaracje zmiennych lokalnych. Można rozszerzyć go do innych `foreach` deklaracji, `for` takich jak pętle, pętle, wyrażenia LINQ i wyrażenia lambda. Ponadto ta przepisana zmieni jedynie deklaracje najprostszej formy:

```csharp
Type variable = expression;
```

Jeśli chcesz eksplorować samodzielnie, należy rozważyć rozszerzenie gotowego przykładu dla tych typów deklaracji zmiennych:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Dodaj następujący kod do treści `VisitLocalDeclarationStatement` metody, aby pominąć przepisywanie tych form deklaracji:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda wskazuje, że nie ma na `node` nowo przepisanie odbywa się przez zwrócenie parametru niezmodyfikowane. Jeśli żadne z `if` tych wyrażeń nie są spełnione, węzeł reprezentuje możliwą deklarację z inicjowaniem. Dodaj te instrukcje, aby wyodrębnić nazwę typu określoną <xref:Microsoft.CodeAnalysis.SemanticModel> w deklaracji i powiązać ją za pomocą pola w celu uzyskania symbolu typu:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Teraz dodaj tę instrukcję, aby powiązać wyrażenie inicjatora:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Na koniec dodaj `if` następującą instrukcję, `var` aby zastąpić istniejącą nazwę typu słowem kluczowym, jeśli typ wyrażenia inicjatora pasuje do określonego typu:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Warunek jest wymagany, ponieważ deklaracja może rzutować wyrażenie inicjatora do klasy podstawowej lub interfejsu. Jeśli jest to pożądane, typy po lewej i prawej stronie przypisania nie są zgodne. Usunięcie jawnego typu w takich przypadkach spowoduje zmianę semantyki programu. `var`jest określony jako identyfikator, a nie `var` słowo kluczowe, ponieważ jest kontekstowe słowo kluczowe. Ciekawostki wiodące i końcowe (biały znak) są przenoszone `var` ze starej nazwy typu do słowa kluczowego w celu zachowania pionowego odstępu i wcięcia. Jest to prostsze w użyciu, `ReplaceNode` a nie `With*` do przekształcania, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> ponieważ nazwa typu jest rzeczywiście wnukiem deklaracji instrukcji.

Zakończyłeś `TypeInferenceRewriter`. Teraz wróć `Program.cs` do pliku, aby zakończyć przykład. Utwórz <xref:Microsoft.CodeAnalysis.Compilation> test i <xref:Microsoft.CodeAnalysis.SemanticModel> uzyskaj z niego. Użyj <xref:Microsoft.CodeAnalysis.SemanticModel> tego, `TypeInferenceRewriter`aby spróbować swojego pliku . Zrobisz ten krok jako ostatni. W międzyczasie zadeklarować zmienną zastępczą reprezentującą kompilację testu:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po wstrzymaniu chwili powinien zostać wyświetlony błąd squiggle pojawiają się raportowanie, że żadna metoda nie `CreateTestCompilation` istnieje. Naciśnij **klawisze Ctrl+Period,** aby otworzyć żarówkę, a następnie naciśnij klawisz Enter, aby wywołać polecenie **Wygeneruj ciąg wycinkowy metody.** To polecenie wygeneruje wycinek metody dla `CreateTestCompilation` metody w `Program` klasie. Wrócisz, aby wypełnić tę metodę później:

![C# Generowanie metody z użycia](./media/syntax-transformation/generate-from-usage.png)

Zapisz następujący kod do iterate nad każdym <xref:Microsoft.CodeAnalysis.SyntaxTree> w teście <xref:Microsoft.CodeAnalysis.Compilation>. Dla każdego z nich, `TypeInferenceRewriter` zainicjować <xref:Microsoft.CodeAnalysis.SemanticModel> nowy z dla tego drzewa:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Wewnątrz `foreach` utworzonej instrukcji dodaj następujący kod, aby wykonać transformację na każdym drzewie źródłowym. Ten kod warunkowo zapisuje nowe przekształcone drzewo, jeśli zostały wprowadzone jakiekolwiek zmiany. Przepisowanie należy modyfikować drzewa tylko wtedy, gdy napotka jedną lub więcej deklaracji zmiennych lokalnych, które mogą być uproszczone przy użyciu wnioskowania o typie:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Pod kodem `File.WriteAllText` powinny być widoczne squiggles. Wybierz żarówkę i dodaj `using System.IO;` niezbędną instrukcję.

Jesteś prawie gotowy! Po raz kolejny pozostało jeszcze <xref:Microsoft.CodeAnalysis.Compilation>krok: utworzenie testu . Ponieważ nie używasz wnioskowania o typie w ogóle podczas tego szybkiego startu, byłoby to doskonały przypadek testowy. Niestety tworzenie kompilacji z pliku projektu C# wykracza poza zakres tego instruktażeu. Ale na szczęście, jeśli uważnie przestrzegałeś instrukcji, jest nadzieja. Zastąp zawartość metody `CreateTestCompilation` następującym kodem. Tworzy kompilację testową, która przypadkowo pasuje do projektu opisanego w tym przewodniku Szybki start:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Trzymajcie kciuki i uruchamiajcie projekt. W programie Visual Studio wybierz pozycję **Debuguj** > **debugowanie rozpocznij debugowanie**. Program Visual Studio powinien monitować o zmianę plików w projekcie. Kliknij przycisk "**Tak dla wszystkich**", aby ponownie załadować zmodyfikowane pliki. Zbadaj je, aby obserwować swoją awesomeness. Należy zauważyć, ile czystsze kod wygląda bez wszystkich tych jawne i nadmiarowe specyfikatory typu.

Gratulacje! Interfejsy **API kompilatora** zostały użyte do napisania własnego refaktoryzacji, który przeszukuje wszystkie pliki w projekcie C# dla niektórych wzorców składni, analizuje semantykę kodu źródłowego, który pasuje do tych wzorców i przekształca go. Jesteś teraz oficjalnie refaktoryzacji autora!
