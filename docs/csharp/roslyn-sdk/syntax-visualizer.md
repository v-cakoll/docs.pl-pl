---
title: Eksploruj kod za pomocą wizualizatora składni Roslyn w programie Visual Studio
description: Wizualizator składni zapewnia narzędzie wizualne do eksplorowania modeli zestawu SDK platformy kompilatora .NET generuje dla kodu.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: 27e5a1f0b31dd2af2ac779223538b03cdb4db0c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156990"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Eksploruj kod za pomocą wizualizatora składni Roslyn w programie Visual Studio

Ten artykuł zawiera omówienie narzędzia wizualizatora składni, które jest dostarczane jako część zestawu SDK platformy kompilatora .NET ("Roslyn"). Wizualizator składni to okno narzędzia, które pomaga sprawdzać i eksplorować drzewa składni. Jest to niezbędne narzędzie do zrozumienia modeli kodu, który chcesz przeanalizować. Jest to również pomoc debugowania podczas tworzenia własnych aplikacji przy użyciu platformy .NET kompilatora ("Roslyn") SDK. Otwórz to narzędzie podczas tworzenia pierwszych analizatorów. Wizualizator pomaga zrozumieć modele używane przez interfejsy API. Można również użyć narzędzi, takich jak [SharpLab](https://sharplab.io) lub [LINQPad,](https://www.linqpad.net/) aby sprawdzić kod i zrozumieć drzewa składni.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Zapoznaj się z pojęciami używanymi w zestawie SDK platformy kompilatora .NET, czytając artykuł [oprzeglądowy.](compiler-api-model.md) Zawiera wprowadzenie do drzewa składni, węzłów, tokenów i ciekawostki.

## <a name="syntax-visualizer"></a>Wizualizator składni

**Wizualizator składni** umożliwia inspekcję drzewa składni dla pliku kodu Języka C# lub Visual Basic w bieżącym oknie edytora aktywnego w ideprogramu Visual Studio. Wizualizator można uruchomić, klikając przycisk **Zobacz** > inne**wizualizacje składni****systemu Windows** > .  Możesz również użyć paska narzędzi **Szybkie uruchamianie** w prawym górnym rogu. Należy wpisać "składnia", a polecenie otwarcia **wizualizatora składni** powinno zostać wyświetlone.

To polecenie otwiera visualizer składni jako okno narzędzia przestawnego. Jeśli nie masz otwartego okna edytora kodu, wyświetlacz jest pusty, jak pokazano na poniższej rysunku.

![Okno narzędzia Wizualizator składni](media/syntax-visualizer/syntax-visualizer.png)

Zadokuj to okno narzędzia w dogodnym miejscu w programie Visual Studio, takim jak lewa strona. Wizualizator pokazuje informacje o bieżącym pliku kodu.

Utwórz nowy projekt przy użyciu polecenia **Plik** > **nowy projekt.** Można utworzyć projekt języka Visual Basic lub C#. Gdy program Visual Studio otwiera główny plik kodu dla tego projektu, wizualizator wyświetla dla niego drzewo składni. W tym wystąpieniu programu Visual Studio można otworzyć dowolny istniejący plik języka C# / Visual Basic, a wizualizator wyświetli drzewo składni tego pliku. Jeśli w programie Visual Studio jest otwartych wiele plików kodu, wizualizator wyświetla drzewo składni aktualnie aktywnego pliku kodu (plik kodu z fokusem klawiatury).

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)
![Wizualizacja drzewa składni Języka C#](media/syntax-visualizer/visualize-csharp.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)
![Wizualizacja drzewa składni języka Visual Basic](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak pokazano na poprzednich obrazach, w oknie narzędzia wizualizatora jest wyświetlane drzewo składni u góry i siatka właściwości u dołu. Siatka właściwości wyświetla właściwości elementu, który jest aktualnie zaznaczony w drzewie, w tym *typ* .NET i *rodzaj* (Składnia) elementu.

Drzewa składni składają się z trzech typów elementów — *węzłów,* *tokenów*i *ciekawostek.* Więcej informacji na temat tych typów można przeczytać w artykule [Praca ze składnią.](work-with-syntax.md) Elementy każdego typu są reprezentowane przy użyciu innego koloru. Kliknij przycisk "Legenda", aby zapoznać się z używanymi kolorami.

Każdy element w drzewie wyświetla również swój własny **zakres**. Zakres **jest** indeksy (pozycja początkowa i końcowa) tego węzła w pliku tekstowym.  W poprzednim przykładzie C# wybrany token "UsingKeyword [0..5)" ma **span,** który ma pięć znaków szerokości [0..5). Notacja "[..)" oznacza, że indeks początkowy jest częścią przedziału, ale indeks końcowy nie jest.

Istnieją dwa sposoby poruszania się po drzewie:

* Rozwiń lub kliknij na elementy w drzewie. Wizualizator automatycznie wybiera tekst odpowiadający zakresowi tego elementu w edytorze kodu.
* Kliknij lub zaznacz tekst w edytorze kodu. W poprzednim przykładzie języka Visual Basic po wybraniu wiersza zawierającego "Module Module1" w edytorze kodu wizualizator automatycznie przechodzi do odpowiedniego węzła ModuleStatement w drzewie.

Wizualizator wyróżnia element w drzewie, którego zakres najlepiej pasuje do zakres tekstu zaznaczonego w edytorze.

Wizualizator odświeża drzewo, aby dopasować modyfikacje w aktywnym pliku kodu. Dodaj połączenie `Console.WriteLine()` do `Main()`środka . Podczas pisania wizualizator odświeża drzewo.

Po wpisaniu wstrzymaj wpisywanie `Console.`tekstu . Drzewo ma kilka przedmiotów w kolorze różowym. W tym momencie występują błędy (określane również jako "Diagnostyka") w wpisanych kodu. Błędy te są dołączone do węzłów, tokenów i ciekawostek w drzewie składni. Wizualizator pokazuje, które elementy mają błędy dołączone do nich podświetlając tło na różowo. Możesz sprawdzić błędy na dowolnym elemencie w kolorze różowym, najeżdżając kursorem na element. Wizualizator wyświetla tylko błędy składni (te błędy związane ze składnią wpisanego kodu); nie wyświetla żadnych błędów semantycznych.

## <a name="syntax-graphs"></a>Wykresy składni

Kliknij prawym przyciskiem myszy dowolny element w drzewie i kliknij **polecenie Wyświetl wykres składni bezpośredniej**.

# <a name="c"></a>[C #](#tab/csharp)

Wizualizator wyświetla graficzną reprezentację poddrzewa zakorzenionego w wybranym elemencie. Spróbuj wykonać te kroki dla węzła `Main()` **MethodDeclaration** odpowiadającego metodzie w przykładzie C#. Wizualizator wyświetla wykres składni, który wygląda następująco:

![Wyświetlanie wykresu składni języka C#](media/syntax-visualizer/csharp-syntax-graph.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

Spróbuj tego samego dla węzła **SubBlock** odpowiadającego metodzie `Main()` w poprzednim przykładzie języka Visual Basic. Wizualizator wyświetla wykres składni, który wygląda następująco:

![Wyświetlanie wykresu składni języka Visual Basic](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Przeglądarka wykresów składni ma opcję wyświetlania legendy jej schemat ubarwiania. Można również najechać kursorem na poszczególne elementy na wykresie składni za pomocą myszy, aby wyświetlić właściwości odpowiadające tej pozycji.

Wykresy składni dla różnych elementów w drzewie można wielokrotnie wyświetlać, a wykresy będą zawsze wyświetlane w tym samym oknie wewnątrz programu Visual Studio. To okno można zadokować w dogodnej lokalizacji w programie Visual Studio, dzięki czemu nie trzeba przełączać się między kartami, aby wyświetlić nowy wykres składni. Na dole, poniżej okien edytora kodu, jest często wygodne.

Oto układ dokowania do użycia z okna narzędzia wizualizatora i okna wykresu składni:

![Jeden układ dokowania okna wykresu wizualizatora i składni](media/syntax-visualizer/docking-layout.png)

Inną opcją jest umieszczenie okna wykresu składni na drugim monitorze, w konfiguracji z dwoma monitorami.

## <a name="inspecting-semantics"></a>Kontrola semantyki

Wizualizator składni umożliwia podstawową inspekcję symboli i informacji semantycznych. Wpisz `double x = 1 + 1;` wewnątrz Main() w przykładzie C#. Następnie wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wizualizator wyróżnia węzeł **AddExpression** w wizualizatorze. Kliknij prawym przyciskiem myszy ten **AddExpression** i kliknij **na Wyświetl symbol (jeśli istnieje)**. Należy zauważyć, że większość elementów menu ma kwalifikator "jeśli istnieje". Dewizual składni sprawdza właściwości węzła, w tym właściwości, które mogą nie być obecne dla wszystkich węzłów.

Siatka właściwości w wizualizatorze aktualizuje się, jak pokazano na poniższej rysunku: Symbol wyrażenia jest **SynthesizedIntrinsicOperatorSymbol** z **Kind = Method**.

![Właściwości symbolu](media/syntax-visualizer/symbol-properties.png)

**Wypróbuj widok TypeSymbol (jeśli istnieje)** dla tego samego **węzła AddExpression.** Siatka właściwości w wizualizatorze zostanie zaktualizowana, jak pokazano na `Int32`poniższym rysunku, wskazując, że typem wybranego wyrażenia jest .

![Właściwości TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

**Wypróbuj widok Przekonwertowany symbol typesymbol (jeśli istnieje)** dla tego samego **węzła AddExpression.** Siatka właściwości jest aktualizowana wskazując, że `Int32`chociaż typem wyrażenia jest `Double` , przekonwertowany typ wyrażenia jest jak pokazano na poniższym rysunku. Ten węzeł zawiera informacje o symbolu konwersji typu, ponieważ `Int32` wyrażenie występuje `Double`w kontekście, w którym musi zostać przekonwertowane na . Ta konwersja `Double` spełnia typ określony `x` dla zmiennej po lewej stronie operatora przypisania.

![Właściwości Konwertowane typesymbol](media/syntax-visualizer/converted-type-symbol-properties.png)

Na koniec spróbuj **wyświetl wartość stałą (jeśli istnieje)** dla tego samego **węzła AddExpression.** Siatka właściwości pokazuje, że wartość wyrażenia jest stałą `2`czasu kompilacji z wartością .

![Stała wartość](media/syntax-visualizer/constant-value.png)

Poprzedni przykład można również replikować w języku Visual Basic. Wpisz `Dim x As Double = 1 + 1` plik języka Visual Basic. Wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wizualizator wyróżnia odpowiedni węzeł **AddExpression** w wizualizatorze. Powtórz poprzednie kroki dla tego **AddExpression** i powinny być widoczne identyczne wyniki.

Sprawdź więcej kodu w języku Visual Basic. Zaktualizuj główny plik języka Visual Basic za pomocą następującego kodu:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Ten kod wprowadza alias `C` o nazwie, `System.Console` który mapuje na typ u `Main()`góry pliku i używa tego aliasu wewnątrz . Wybierz użycie tego aliasu, in `C` `C.WriteLine()` `Main()` , wewnątrz metody. Wizualizator wybiera odpowiedni węzeł **IdentifierName** w wizualizatorze. Kliknij prawym przyciskiem myszy ten węzeł i kliknij polecenie **Wyświetl symbol (jeśli istnieje).** Siatka właściwości wskazuje, że ten identyfikator `System.Console` jest powiązany z typem, jak pokazano na poniższym rysunku:

![Właściwości symbolu](media/syntax-visualizer/symbol-visual-basic.png)

**Wypróbuj wyświetl aliassymbol (jeśli istnieje)** dla tego samego **węzła IdentifierName.** Siatka właściwości wskazuje, że identyfikator jest `C` aliasem `System.Console` o nazwie powiązanej z obiektem docelowym. Innymi słowy siatka właściwości zawiera informacje dotyczące **AliasSymbol** `C`odpowiadające identyfikatorowi .

![Właściwości AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Sprawdź symbol odpowiadający dowolnemu typowi zadeklarowanemu, metodzie, właściwości. Wybierz odpowiedni węzeł w wizualizatorze i kliknij **na Wyświetl symbol (jeśli istnieje)**. Wybierz metodę `Sub Main()`, w tym treść metody. Kliknij **na Wyświetl symbol (jeśli istnieje)** dla odpowiedniego **węzła SubBlock** w wizualizatorze. Siatka właściwości pokazuje **MethodSymbol** dla tego `Main` **podbloku** ma nazwę z typem `Void`zwracania .

![Wyświetlanie symbolu deklaracji metody](media/syntax-visualizer/method-symbol.png)

Powyższe przykłady języka Visual Basic można łatwo replikować w języku C#. Wpisz `using C = System.Console;` w `Imports C = System.Console` miejsce aliasu. Poprzednie kroki w języku C# dają identyczne wyniki w oknie wizualizatora.

Operacje inspekcji semantycznej są dostępne tylko w węzłach. Nie są one dostępne na tokenach ani ciekawostkach. Nie wszystkie węzły mają interesujące informacje semantyczne do sprawdzenia. Jeśli węzeł nie zawiera interesujących informacji semantycznych, kliknięcie **symbolu widoku \* (jeśli istnieje)** pokazuje pustą siatkę właściwości.

Więcej informacji na temat interfejsów API do wykonywania analizy semantycznej można przeczytać w dokumencie przegląd pracy [z semantyką.](work-with-semantics.md)

## <a name="closing-the-syntax-visualizer"></a>Zamykanie wizualizatora składni

Okno wizualizatora można zamknąć, gdy nie używasz go do badania kodu źródłowego. Wizualizator składni aktualizuje jego wyświetlanie podczas poruszania się po kodzie, edytowaniu i zmienianiu źródła. Może się rozpraszać, gdy go nie używasz.
