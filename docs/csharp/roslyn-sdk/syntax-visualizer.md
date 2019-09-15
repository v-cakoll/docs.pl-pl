---
title: Eksplorowanie kodu za pomocą wizualizatora składni Roslyn w programie Visual Studio
description: Wizualizator składni zawiera narzędzie wizualne umożliwiające Eksplorowanie modeli, które zestaw .NET Compiler Platform SDK generuje dla kodu.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: fa3b4fdbb8d573805119e13e8aa93f156c4111f9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972016"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Eksplorowanie kodu za pomocą wizualizatora składni Roslyn w programie Visual Studio

Ten artykuł zawiera omówienie narzędzia Syntax Visualizer, które jest dostarczane jako część .NET Compiler Platform ("Roslyn") SDK. Syntax Visualizer jest oknem narzędzi, które ułatwia sprawdzanie i eksplorowanie drzew składni. Jest to podstawowe narzędzie do zrozumienia modeli dla kodu, który ma zostać przeanalizowany. Jest to również pomoc dla debugowania podczas tworzenia własnych aplikacji przy użyciu zestawu SDK .NET Compiler Platform ("Roslyn"). Otwórz to narzędzie podczas tworzenia pierwszych analizatorów. Wizualizator pomaga zrozumieć modele używane przez interfejsy API. Możesz również użyć narzędzi, takich jak [SharpLab](https://sharplab.io) lub [LINQPad](https://www.linqpad.net/) , aby sprawdzić kod i zrozumieć drzewa składniowe.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Zapoznaj się z pojęciami użytymi w zestawie SDK .NET Compiler Platform, odczytując artykuł z [omówieniem](compiler-api-model.md) . Zawiera wprowadzenie do drzew składni, węzłów, tokenów i kwizy.

## <a name="syntax-visualizer"></a>Syntax Visualizer

**Syntax Visualizer** umożliwia inspekcję drzewa składni dla C# pliku kodu w języku vb w bieżącym aktywnym oknie edytora w środowisku IDE programu Visual Studio. Wizualizator można uruchomić, klikając pozycję **Wyświetl** > **inne okna** > **Syntax Visualizer**.  Możesz również użyć paska narzędzi **Szybkie uruchamianie** w prawym górnym rogu. Wpisz "składnia" i polecenie, aby otworzyć **Syntax Visualizer** powinna zostać wyświetlona.

To polecenie otwiera Syntax Visualizer jako okno narzędzi zmiennoprzecinkowych. Jeśli nie masz otwartego okna edytora kodu, ekran jest pusty, jak pokazano na poniższej ilustracji. 

![Okno narzędzia Syntax Visualizer](media/syntax-visualizer/syntax-visualizer.png)

Zadokuj to okno narzędzia w wygodnej lokalizacji wewnątrz programu Visual Studio, na przykład po lewej stronie. Wizualizator pokazuje informacje o bieżącym pliku kodu.

Utwórz nowy projekt za pomocą polecenia **plik** > **Nowy projekt** . Można utworzyć projekt w języku VB lub C# . Gdy program Visual Studio otwiera główny plik kodu dla tego projektu, wizualizator Wyświetla drzewo składni. Można otworzyć każdy istniejący C# plik/VB w tym wystąpieniu programu Visual Studio, a wizualizator Wyświetla drzewo składni tego pliku. Jeśli masz otwartych wiele plików kodu w programie Visual Studio, wizualizatorer Wyświetla drzewo składni dla aktualnie aktywnego pliku kodu (plik kodu z fokusem klawiatury).

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Wizualizowanie drzewa C# składni](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
![Wizualizowanie drzewa składni języka VB](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak pokazano na powyższym obrazie, okno narzędzia wizualizatora Wyświetla drzewo składni u góry i siatkę właściwości u dołu. Siatka właściwości zawiera właściwości elementu, który jest aktualnie wybrany w drzewie, w tym *Typ* .NET i *rodzaj* (elementem syntaxkind) elementu.

Drzewa składni składają się z trzech typów elementów — *węzłów*, *tokenów*i *kwizy*. Więcej informacji na temat tych typów można znaleźć w artykule dotyczącym [składni](work-with-syntax.md) . Elementy każdego typu są reprezentowane przy użyciu innego koloru. Kliknij przycisk "Legenda", aby zapoznać się z omówieniem użytych kolorów.

Każdy element w drzewie również Wyświetla własny **zakres**. **Zakres** jest indeksem (położenie początkowe i końcowe) tego węzła w pliku tekstowym.  W powyższym C# przykładzie, wybrany token "UsingKeyword [0.. 5)" ma **zakres** , który ma pięć znaków szerokości, [0.. 5). Notacja "[...)" oznacza, że indeks początkowy jest częścią zakresu, ale końcowym indeksem nie jest.

Istnieją dwa sposoby nawigowania po drzewie:

* Rozwiń lub kliknij elementy w drzewie. Wizualizator automatycznie zaznaczy tekst odpowiadający zakresowi tego elementu w edytorze kodu.
* Kliknij lub zaznacz tekst w edytorze kodu. W poprzednim przykładzie w języku VB w przypadku wybrania w edytorze kodu wiersza zawierającego "module Module1" wizualizator automatycznie nawiguje do odpowiedniego węzła ModuleStatement w drzewie. 

Wizualizator podświetla element w drzewie, którego zakres najlepiej pasuje do zakresu tekstu zaznaczonego w edytorze.

Wizualizator odświeża drzewo, aby dopasować modyfikacje w aktywnym pliku kodu. Dodaj wywołanie do `Console.WriteLine()` wewnątrz `Main()`. Podczas wpisywania, wizualizator odświeża drzewo.

Wstrzymaj wpisywanie po wpisaniu `Console.`. Drzewo ma pewne elementy kolorowe w kolorze różowym. W tym momencie istnieją błędy (nazywane również "diagnostyką") w określonym kodzie. Te błędy są dołączone do węzłów, tokenów i kwizy w drzewie składni. Wizualizator pokazuje, które elementy zawierają błędy dołączone do nich, podkreślając tło w kolorze różowym. Błędy w dowolnym elemencie można sprawdzić kolorem różowym, umieszczając kursor na elemencie. Wizualizator wyświetla tylko błędy składni (te błędy związane ze składnią wpisanego kodu); nie są wyświetlane żadne błędy semantyczne.
 
## <a name="syntax-graphs"></a>Wykresy składniowe

Kliknij prawym przyciskiem myszy dowolny element w drzewie, a następnie kliknij polecenie **Wyświetl wykres Pokierowanej składni**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Wizualizator Wyświetla graficzną reprezentację poddrzewa osadzonego na wybranym elemencie. Spróbuj wykonać następujące kroki dla węzła **MethodDeclaration** odpowiadającego `Main()` metodzie w C# przykładzie. Wizualizator wyświetla wykres składni, który wygląda następująco:

![Wyświetlanie grafu C# składni](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Wypróbuj te same dla węzła **bloku** podrzędnego odpowiadającego `Main()` metodzie w poprzednim przykładzie w języku VB. Wizualizator wyświetla wykres składni, który wygląda następująco:

![Wyświetlanie grafu składni VB](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Przeglądarka grafu składni zawiera opcję wyświetlania legendy jej schematu kolorowania. Możesz również umieścić wskaźnik myszy nad poszczególnymi elementami na wykresie składni, aby wyświetlić właściwości odpowiadające temu elementowi.

Wykresy składniowe można wyświetlać wielokrotnie dla różnych elementów w drzewie, a wykresy będą zawsze wyświetlane w tym samym oknie w programie Visual Studio. To okno można zadokować w wygodnej lokalizacji wewnątrz programu Visual Studio, aby nie trzeba było przełączać się między kartami, aby wyświetlić nowy wykres składni. Dolna, poniżej okna edytora kodu, jest często wygodna.

Poniżej znajduje się układ dokowania, który ma być używany z oknem narzędzia wizualizatora oraz oknem grafu składni:

![Jeden układ dokowania dla wizualizatora i okna wykresu składniowego](media/syntax-visualizer/docking-layout.png)

Innym rozwiązaniem jest umieszczenie okna wykresu składniowego na drugim monitorze w konfiguracji podwójnego monitora.

## <a name="inspecting-semantics"></a>Sprawdzanie semantyki

Syntax Visualizer umożliwia inspekcję podstawowe symboli i informacji semantycznych. W `double x = 1 + 1;` C# przykładzie wpisz wewnątrz Main (). Następnie wybierz wyrażenie `1 + 1` w oknie Edytor kodu. Wizualizator podświetla węzeł **AddExpression** w wizualizatorze. Kliknij prawym przyciskiem myszy to polecenie **AddExpression** i kliknij pozycję **Wyświetl symbol (jeśli istnieje)** . Należy zauważyć, że większość elementów menu ma kwalifikator "Jeśli any". Syntax Visualizer sprawdza właściwości węzła, w tym właściwości, które mogą nie być obecne dla wszystkich węzłów. 

Siatka właściwości w ramach aktualizacji wizualizatora, jak pokazano na poniższej ilustracji: Symbol wyrażenia jest **SynthesizedIntrinsicOperatorSymbol** z **typem = Method**.

![Właściwości symbolu](media/syntax-visualizer/symbol-properties.png)

Spróbuj **wyświetlić TypeSymbol (jeśli istnieje)** dla tego samego węzła **AddExpression** . Siatka właściwości na stronie wizualizatora aktualizuje, jak pokazano na poniższej ilustracji, co oznacza, że typ wybranego wyrażenia to `Int32`.

![Właściwości TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Spróbuj **wyświetlić przekonwertowane TypeSymbol (jeśli istnieje)** dla tego samego węzła **AddExpression** . Aktualizacja siatki właściwości wskazująca, że chociaż typ wyrażenia to `Int32`, przekonwertowanego typu wyrażenia jest `Double` tak jak pokazano na poniższym rysunku. Ten węzeł zawiera informacje o symbolach konwersji, `Int32` ponieważ wyrażenie występuje w kontekście, w którym musi zostać przekonwertowane `Double`na. Ta konwersja spełnia `Double` typ określony dla zmiennej `x` po lewej stronie operatora przypisania.

![Skonwertowane właściwości TypeSymbol](media/syntax-visualizer/converted-type-symbol-properties.png)

Na koniec spróbuj **wyświetlić wartość stałą (jeśli istnieje)** dla tego samego węzła **AddExpression** . Siatka właściwości pokazuje, że wartość wyrażenia jest stałą czasu kompilacji o wartości `2`.

![Stała wartość](media/syntax-visualizer/constant-value.png)

Poprzedni przykład można także zreplikować w języku VB. Wpisz `Dim x As Double = 1 + 1` plik w języku VB. Wybierz wyrażenie `1 + 1` w oknie Edytor kodu. Wizualizator podświetla odpowiadający jej węzeł **AddExpression** w wizualizatorze. Powtórz powyższe kroki dla tego **AddExpression** i powinny być widoczne identyczne wyniki.

Zapoznaj się z kodem w języku VB. Zaktualizuj główny plik VB przy użyciu następującego kodu:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Ten kod wprowadza alias o nazwie `C` , który jest mapowany na `System.Console` typ w górnej części pliku i używa tego aliasu wewnątrz `Main()`. Wybierz użycie tego aliasu `C` w `C.WriteLine()`, wewnątrz `Main()` metody. Wizualizator wybiera odpowiedni węzeł **identyfikatorname** w wizualizatorze. Kliknij prawym przyciskiem myszy ten węzeł i kliknij pozycję **Wyświetl symbol (jeśli istnieje)** . Siatka właściwości wskazuje, że ten identyfikator jest powiązany z typem `System.Console` , jak pokazano na poniższym rysunku:

![Właściwości symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Spróbuj **wyświetlić AliasSymbol (jeśli istnieje)** dla tego samego węzła **identyfikatoraname** . Siatka właściwości wskazuje, że identyfikator jest alias o nazwie `C` , która jest powiązana `System.Console` z obiektem docelowym. Innymi słowy, Siatka właściwości zawiera informacje dotyczące **AliasSymbol** odpowiadającego identyfikatorowi `C`.

![Właściwości AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Zbadaj Symbol odpowiadający każdemu zadeklarowanemu typowi, metodzie, właściwości. Wybierz odpowiedni węzeł w wizualizatorze i kliknij pozycję **Wyświetl symbol (jeśli istnieje)** . Wybierz metodę `Sub Main()`, łącznie z treścią metody. Kliknij pozycję **Wyświetl symbol (jeśli istnieje)** **dla odpowiedniego węzła** podrzędnego w wizualizatorze. Siatka właściwości pokazuje **MethodSymbol** dla tego **podbloku** ma nazwę `Main` z typem `Void`zwracanym.

![Wyświetlanie symbolu dla deklaracji metody](media/syntax-visualizer/method-symbol.png)

Powyższe przykłady w języku VB mogą być łatwo zreplikowane C#w programie. `using C = System.Console;` Wpisz`Imports C = System.Console` miejsce dla aliasu. Powyższe kroki w programie C# dają identyczne wyniki w oknie wizualizatora.

Operacje inspekcji semantycznej są dostępne tylko w węzłach. Nie są one dostępne w tokenach ani kwizy. Nie wszystkie węzły mają interesujące informacje semantyczne do sprawdzenia. Gdy węzeł nie ma interesujących informacji semantycznych, kliknięcie **pozycji \* Wyświetl symbol (jeśli istnieje)** powoduje wyświetlenie pustej siatki właściwości.

Więcej informacji na temat interfejsów API do wykonywania analizy semantycznej można znaleźć w dokumencie przegląd [pracy z semantyką](work-with-semantics.md) .

## <a name="closing-the-syntax-visualizer"></a>Zamykanie wizualizatora składni

Okno wizualizatorer można zamknąć, gdy nie jest używane do badania kodu źródłowego. Wizualizator składni aktualizuje swój ekran podczas poruszania się po kodzie, edycji i zmieniania źródła. Może to odwrócić, gdy nie jest używany. 
