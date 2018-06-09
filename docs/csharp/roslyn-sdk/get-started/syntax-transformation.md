---
title: Wprowadzenie do przekształcania składni (Roslyn API)
description: Wprowadzenie do przechodzenie, zapytań i przejście drzewa składni.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 04053645b91e8f74e890340fb9bba66a4efdce0c
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231631"
---
# <a name="get-started-with-syntax-transformation"></a>Wprowadzenie do przekształcania składni

W tym samouczku opiera się na koncepcji i technik przedstawione w [wprowadzenie do analizy składni](syntax-analysis.md) i [wprowadzenie do analizy semantycznego](semantic-analysis.md) Przewodniki Szybki Start. Jeśli nie jest jeszcze tych skróconych podręczników należy wykonać przed rozpoczęciem tego.

Ta opcja szybkiego startu służy do eksplorowania technik tworzenia i przekształcanie drzewa składni. W połączeniu z metod, które uzyskanych w poprzednim poradniki Szybki Start możesz utworzyć Twojego pierwszego wiersza polecenia refaktoryzacji!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Immutability i kompilatora platformy .NET

**Immutability** jest podstawowych cechą kompilatora platformy .NET. Nie można zmienić struktury modyfikować danych, po są tworzone. Bezpiecznie udostępnione struktur danych niezmienne i analizowane przez wielu klientów jednocześnie. Istnieje niebezpieczeństwo tego jednego użytkownika wpływ na inną w sposób nieprzewidywalny. Twoje analizatora nie wymaga blokady lub innych środków współbieżności. Ta reguła ma zastosowanie do drzewa składni, kompilacji, symbole, modeli semantycznych i co inne struktury danych, które wystąpią. Zamiast zmodyfikowanie istniejącej struktury, interfejsy API tworzenia nowych obiektów, oparte na określonej różnice do starych. To pojęcie dotyczą drzewa składni do utworzenia nowego drzew używanie przekształceń.

## <a name="create-and-transform-trees"></a>Tworzenie i przekształcanie drzewa.

Możesz wybrać jeden z dwóch strategii składnia przekształcenia. **Metody fabryki** najlepiej są używane, gdy szukasz określonych węzłów w celu zastąpienia lub określonych lokalizacji, w której chcesz wstawić nowy kod. **Rewriters** są najlepiej, gdy chcesz skanować całego projektu dla wzorców kodu, które mają zostać zamienione.

### <a name="create-nodes-with-factory-methods"></a>Utwórz węzły z metodami factory

Pierwszy przekształcania składni przedstawiono metody fabryki. Zamierzasz zamienić `using System.Collections;` instrukcji z `using System.Collections.Generic;` instrukcji. W tym przykładzie pokazano, jak utworzyć <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> obiektów przy użyciu <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody fabryki. Dla każdego rodzaju z **węzła**, **tokenu**, lub **elementy towarzyszące składni** istnieje metoda fabryki, która tworzy wystąpienie tego typu. Można utworzyć drzewa składni za tworzenie węzłów w hierarchii zgodnie z dołu do góry. Następnie będzie przekształcenie istniejący program można zastępowanie istniejących węzłów z nowym drzewie po utworzeniu.

Uruchom program Visual Studio i utworzyć nowe C# **autonomiczne narzędzie do analizy kodu** projektu. W programie Visual Studio, wybierz **pliku** > **nowy* > **projektu** do wyświetlenia w oknie dialogowym Nowy projekt. W obszarze **Visual C#** > **rozszerzalności** wybierz **autonomiczne narzędzie do analizy kodu**. Ta opcja szybkiego startu zawiera dwa projekty przykład, więc nazwa rozwiązania **SyntaxTransformationQuickStart**i nazwij projekt **ConstructionCS**. Kliknij przycisk **OK**.

Ten projekt używa <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody do utworzenia klasy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> reprezentujący `System.Collections.Generic` przestrzeni nazw.

Dodaj następujący kod przy użyciu dyrektywy na początku `Program.cs` plik do zaimportowania metody fabryki <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> klasy i metody <xref:System.Console> tak, aby można je później użyć bez kwalifikujących się je:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Utworzysz **nazwy węzłów składni** do tworzenia drzewa, który reprezentuje `using System.Collections.Generic;` instrukcji. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> jest klasą bazową dla cztery typy nazw, które są wyświetlane w języku C#. Możesz utworzyć te cztery typy nazwy, aby utworzyć dowolną nazwę, które mogą być wyświetlane w języku C#:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, reprezentuje nazwy proste pojedynczy identyfikator, takie jak `System` i `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, takich jak reprezentuje nazwy typu lub metody ogólnej `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, reprezentuje nazwę kwalifikowaną formularza `<left-name>.<right-identifier-or-generic-name>` takich jak `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, który reprezentuje nazwę przy użyciu zestawu extern alias takich `LibraryV2::Foo`.

Możesz użyć <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> metodę w celu utworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> węzła. Dodaj następujący kod w Twojej `Main` metody w `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Poprzedni kod tworzy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> obiektów i przypisuje go do zmiennej `name`. Zwraca wiele interfejsów API Roslyn klas podstawowych, aby ułatwić pracę z typami pokrewne. Zmienna `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, mogą być ponownie używane podczas tworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nie używaj wnioskowanie o typie, podczas tworzenia przykładowej. Będzie zautomatyzować tego kroku w tym projekcie.

Po utworzeniu nazwy. Teraz nadszedł czas na wbudowanie większą liczbę węzłów w drzewie według budynków <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Używa nowego drzew `name` od lewej nazwy i nowego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> dla `Collections` obszaru nazw po prawej stronie <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Dodaj następujący kod do `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Ponownie uruchom kod i wyświetlić wyniki. Tworzysz drzewo węzłów reprezentuje kod. Będzie to wzorzec do tworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> dla przestrzeni nazw `System.Collections.Generic`. Dodaj następujący kod do `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Uruchom program ponownie, aby zobaczyć, czy zostały kompilacji drzewa dla kodu w celu dodania.

### <a name="create-a-modified-tree"></a>Tworzenie zmodyfikowane drzewa

Został utworzony drzewa składni małych, który zawiera jedną instrukcję. Interfejsy API, aby utworzyć nowe węzły są właściwie utworzyć jednej instrukcji lub inne bloki mały kod. Jednak aby utworzyć większe bloki kodu, należy używać metody Zastąp węzłów lub wstawić węzłów do istniejącego drzewa. Pamiętaj, że drzewa składni jest niezmienialny. **API składni** nie zapewnia żadnych mechanizmu modyfikowania istniejącego drzewa składni po wykonaniu konstrukcji. Przekazuje on metod, które powodują powstanie nowego drzew na podstawie zmian w istniejących. `With*` metody są zdefiniowane w klas konkretnych wywodzących się z <xref:Microsoft.CodeAnalysis.SyntaxNode> lub rozszerzenia metod zadeklarowanych w <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> klasy. Te metody Utwórz nowy węzeł, wprowadzając zmiany w istniejących węzłów podrzędnych właściwości. Ponadto <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> — metoda rozszerzenia może być używany do zastąpienia węzeł podrzędny w poddrzewo. Ta metoda również aktualizuje element nadrzędny, aby wskazywały nowo utworzony element podrzędny i proces ten zapasową całego drzewa — proces znany jako _spining ponowna_ drzewa.

Następnym krokiem jest tworzenie drzewa, który reprezentuje cały (mały) program, a następnie zmodyfikować go. Dodaj następujący kod na początku `Program` klasy:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Przykład kodu wykorzystuje `System.Collections` przestrzeni nazw i nie `System.Collections.Generic` przestrzeni nazw.

Następnie dodaj następujący kod do dołu `Main` metody, można przeanalizować tekstu i utworzyć drzewo:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

W tym przykładzie użyto <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> metodę, aby zastąpić nazwę w <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> węzła z elementem utworzone w poprzednim kodzie.

Utwórz nową <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> za pomocą węzła <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> metodę aktualizowania `System.Collections` nazwa o nazwie utworzonego w poprzednim kodzie. Dodaj następujący kod do dołu `Main` metody:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Uruchom program i sprawdź dokładnie w danych wyjściowych. `newusing` Nie została umieszczona w drzewie katalogu głównego. Oryginalny drzewa nie został zmodyfikowany.

Dodaj następujący kod przy użyciu <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metodę rozszerzenie w celu utworzenia nowego drzewa. Nowe drzewo jest wynikiem zastępowanie istniejących importu zaktualizowanego `newUsing` węzła. Przypisz tego nowego drzew do istniejącego `root` zmienną:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Ponownie uruchom program. Teraz drzewa teraz prawidłowo importuje `System.Collections.Generic` przestrzeni nazw.

### <a name="transform-trees-using-syntaxrewriters"></a>Przekształcanie przy użyciu drzewa `SyntaxRewriters`

`With*` i <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metody udostępniają wygodny sposób Przekształcanie poszczególnych gałęziach drzewa składni. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Klasa wykonuje wiele przekształcenia na drzewie składni. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Klasy jest podklasą <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Stosuje przekształcenia do określonego typu <xref:Microsoft.CodeAnalysis.SyntaxNode>. Przekształcenia można stosować do wielu rodzajów <xref:Microsoft.CodeAnalysis.SyntaxNode> obiekty wszędzie tam, gdzie znajdują się w drzewie składni. Drugi projektu w tym szybkiego startu tworzy wiersza polecenia refaktoryzacji, która usuwa jawnie typów w deklaracjach zmiennych lokalnych, może być używane tam, gdzie wnioskowanie typu.

Tworzenie nowych C# **autonomiczne narzędzie do analizy kodu** projektu. W programie Visual Studio, kliknij prawym przyciskiem myszy `SyntaxTransformationQuickStart` węzła rozwiązania. Wybierz **Dodaj** > **nowy projekt** do wyświetlenia **okno dialogowe Nowy projekt**. W obszarze **Visual C#** > **rozszerzalności**, wybierz **autonomiczne narzędzie do analizy kodu**. Nazwij swój projekt `TransformationCS` i kliknij przycisk OK.

Pierwszym krokiem jest utworzenie klasy, która jest pochodną <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> wykonania przekształcenia użytkownika. Dodaj nowy plik klasy do projektu. W programie Visual Studio, wybierz **projektu** > **Dodawanie klasy...** . W **Dodaj nowy element** typu okna dialogowego `TypeInferenceRewriter.cs` jako nazwę pliku.

Dodaj następujący kod przy użyciu dyrektywy `TypeInferenceRewriter.cs` pliku:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Następnie należy `TypeInferenceRewriter` klasa rozszerza <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> klasy:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Dodaj następujący kod, aby zadeklarować prywatnej pola tylko do odczytu do przechowywania <xref:Microsoft.CodeAnalysis.SemanticModel> i zainicjować go w konstruktorze. Będą potrzebne później, aby określić, których można użyć wnioskowanie o typie:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Zastąpienie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metody:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Zwracane typy, które są klas podstawowych typów środowiska uruchomieniowego rzeczywiste zwróconych wiele interfejsów API Roslyn zadeklarować. n wiele scenariuszy, może być zastąpiony przez inny rodzaj węzła całkowicie — lub nawet usunąć jeden rodzaj węzła. W tym przykładzie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda zwraca <xref:Microsoft.CodeAnalysis.SyntaxNode>, zamiast typu pochodnego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Zwraca nowy tej funkcji ponownego zapisu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> istniejącą oparte na węzłach.

Ta opcja szybkiego startu obsługuje deklaracji zmiennych lokalnych. Można rozszerzyć do innych deklaracji takich jak `foreach` pętle, `for` pętle, wyrażenia LINQ i wyrażenia lambda. Ponadto tej funkcji ponownego zapisu tylko przekształci deklaracje najprostsza forma:

```csharp
Type variable = expression;
```

Jeśli chcesz rozpocząć eksplorowanie na własną, należy wziąć pod uwagę rozszerzanie gotowej próbki dla tych typów w deklaracjach zmiennych:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Dodaj następujący kod do treści `VisitLocalDeclarationStatement` metodę, aby pominąć ponowne zapisywanie formach deklaracje:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda wskazuje, że nie ponowne zapisywanie odbywa się zwracając `node` parametru nie mają być modyfikowane. Jeśli żadna z tych `if` wyrażenia mają wartość true, węzeł reprezentuje deklaracji możliwe z inicjowania. Dodaj tych instrukcji do wyodrębnienia Nazwa typu określony w deklaracji i powiąż go przy użyciu <xref:Microsoft.CodeAnalysis.SemanticModel> pola, aby uzyskać symbol typu:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Teraz Dodaj tej instrukcji można powiązać wyrażenia inicjatora:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Na koniec należy dodać następujące `if` instrukcji, aby zastąpić istniejącą nazwę typu z `var` — słowo kluczowe, jeśli typ wyrażenia inicjatora pasuje do typu określonego:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

Warunkowe jest wymagana, ponieważ deklaracja może oddać wyrażenia inicjatora klasy podstawowej lub interfejsu. W razie potrzeby które nie są zgodne typy po lewej i prawej stronie przypisania. Usuwanie jawnego typu w tych przypadkach zmieniłby semantykę programu. `var` jest określony jako identyfikator zamiast słowo kluczowe, ponieważ `var` jest kontekstowe słowo kluczowe. Wiodące i końcowe elementy towarzyszące składni (spacji) są przekazywane z starej nazwy typu `var` — słowo kluczowe utrzymywać odstępy w pionie i wcięcia. Jest łatwiejsze do użycia w `ReplaceNode` zamiast `With*` do przekształcania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> ponieważ nazwa typu jest rzeczywiście podwójnym instrukcji deklaracji.

Znasz Zakończono `TypeInferenceRewriter`. Teraz wróć do Twojej `Program.cs` plik, aby zakończyć w przykładzie. Tworzenie nowego testu <xref:Microsoft.CodeAnalysis.Compilation> i uzyskiwanie <xref:Microsoft.CodeAnalysis.SemanticModel> od niego. Użyj <xref:Microsoft.CodeAnalysis.SemanticModel> próby Twojej `TypeInferenceRewriter`. Ostatnio należy wykonać ten krok. W tym czasie zadeklarować zmiennej symbol zastępczy reprezentujący użytkownika testu kompilacji:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po wstrzymaniu chwilę, powinien zostać wyświetlony wężyk błąd, są wyświetlane raportowania, który nie `CreateTestCompilation` istnieje metoda. Naciśnij klawisz **Ctrl + kropka** Otwórz żarówki, a następnie naciśnij klawisz Enter, aby wywołać **generowania szkieletu metody** polecenia. To polecenie spowoduje wygenerowanie szkieletu metody dla `CreateTestCompilation` metoda `Program` klasy. Użytkownik będzie wróć do wypełnienia później w ramach tej metody:

![C# Generowanie metody z użycia](./media/syntax-transformation/generate-from-usage.png)

Następujący kod, aby przejść przez każdego zapisu <xref:Microsoft.CodeAnalysis.SyntaxTree> w teście <xref:Microsoft.CodeAnalysis.Compilation>. Dla każdego z nich, zainicjować nowe `TypeInferenceRewriter` z <xref:Microsoft.CodeAnalysis.SemanticModel> dla tego drzewa:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Wewnątrz `foreach` instrukcji został utworzony, Dodaj następujący kod do wykonania transformację w każdym drzewie źródła. Ten kod warunkowo zapisuje się nowe drzewo przekształcone dokonane zmiany. Z funkcji ponownego zapisu tylko należy zmodyfikować drzewo, jeśli wykryje co najmniej jeden lokalny deklaracji zmiennych, które można uprościć przy użyciu wnioskowanie o typie:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Powinny pojawić się zygzaki w obszarze `File.WriteAllText` kodu. Wybierz żarówkę, a następnie dodaj niezbędne `using System.IO;` instrukcji.

Prawie gotowe! Raz jest kroku po lewej: tworzenie testu <xref:Microsoft.CodeAnalysis.Compilation>. Ponieważ nie zostały używane wnioskowanie o typie w ogóle podczas tego przewodnika Szybki Start, czy zostały wprowadzone doskonałe przypadkiem testowym. Niestety tworzenie kompilacji z pliku projektu C# wykracza poza zakres tego przewodnika. Na szczęście, jeśli możesz już został instrukcjami dokładnie, występują jednak mamy nadzieję, że. Zastąp zawartość `CreateTestCompilation` metodę z następującym kodem. Tworzy kompilacji testu, przypadkowo odpowiadającego projektu opisane w tym Szybki Start:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Krzyżowe palcami i uruchomić projekt. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie**. Trzeba monitować przez program Visual Studio, które zostały zmienione pliki w projekcie. Kliknij przycisk "**tak, aby wszystkie**" Aby ponownie załadować zmodyfikowane pliki. Przeanalizowanie obserwować awesomeness użytkownika. Należy pamiętać, ile czyściciel kod wygląda bez tych specyfikatory typu explicit oraz nadmiarowe.

Gratulacje! Używano **API kompilatora** zapisu własne refaktoryzacji elementu przeszukuje wszystkie pliki w projekcie C# dla niektórych składni wzorce analizuje semantykę kod źródłowy, który odpowiada tych wzorców i przekształca je. Autor teraz jest oficjalnie refaktoryzacji!