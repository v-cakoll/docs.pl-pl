---
title: 'Przewodnik: Programowanie Office (C# i Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: a9b7a32cc3eb9d65b7c4a8e241eedca14cbf11bb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398159"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Przewodnik: Programowanie Office (C# i Visual Basic)

Visual Studio oferuje funkcje w języku C# i Visual Basic, które zwiększają programowania Microsoft Office. Przydatne funkcje języka C# zawierają argumenty nazwane i opcjonalne i zwracanie wartości typu `dynamic`. W programowaniu modelu COM, można pominąć `ref` — słowo kluczowe i uzyskanie dostępu do właściwości indeksowanych. Funkcje w języku Visual Basic obejmują automatycznie implementowane właściwości instrukcji w wyrażeniach lambda i inicjatory kolekcji.

Obu językach umożliwiają osadzanie informacji o typie, który umożliwia wdrożenie zestawów, które współdziałają ze składnikami modelu COM. bez wdrażania podstawowych zestawów międzyoperacyjnych (PIA) na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [instruktażu: Osadzanie typów z zarządzanych zestawów](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).

W tym instruktażu przedstawiono te funkcje w kontekście programowania pakietu Office, ale wiele z tych funkcji są także przydatne, ogólnie rzecz biorąc programowania. W instruktażu użyjesz aplikacji dodatek programu Excel do utworzenia skoroszytu programu Excel. Następnie należy utworzyć dokument programu Word, zawierającą łącze do skoroszytu. Na koniec zobaczysz, jak włączać i wyłączać zależności PIA.

## <a name="prerequisites"></a>Wymagania wstępne

Konieczne jest posiadanie Microsoft Office Excel i Microsoft Office Word zainstalowana na danym komputerze, w tym przewodniku.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Aby skonfigurować aplikację dodatek programu Excel

1. Uruchom program Visual Studio.

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W **zainstalowane szablony** okienku rozwiń **języka Visual Basic** lub **Visual C#** , rozwiń węzeł **Office**, a następnie kliknij przycisk rok wersji Produkt Office.

4. W **szablony** okienku kliknij **Excel \<wersji > dodatku**.

5. Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4**, lub jego nowsza wersja jest wyświetlana w **platformę docelową** pole.

6. Wpisz nazwę dla projektu w **nazwa** polu, jeśli chcesz.

7. Kliknij przycisk **OK**.

8. Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.

### <a name="to-add-references"></a>Aby dodać odwołania

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** pojawi się okno dialogowe.

2. Na **zestawy** zaznacz **Microsoft.Office.Interop.Excel**, wersja `<version>.0.0.0` (dla klucza do numerów wersji produktów pakietu Office, zobacz [Versions Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)) w polu **nazwa składnika** listy, a następnie przytrzymaj naciśnięty klawisz CTRL, klucza i wybierz pozycję **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Jeśli nie ma zestawów, może być konieczne upewnić się, są zainstalowane i wyświetlane (zobacz [jak: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. Kliknij przycisk **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Aby dodać niezbędne instrukcje import lub dyrektywy using

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisAddIn.vb** lub **ThisAddIn.cs** pliku, a następnie kliknij przycisk **Wyświetl kod**.

2. Dodaj następujący kod `Imports` instrukcji (Visual Basic) lub `using` dyrektywy (C#) na początku pliku kodu, jeśli nie są one już obecne.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **klasy**. Nazwa klasy Account.vb, jeśli używasz języka Visual Basic lub Account.cs Jeśli używasz języka C#. Kliknij przycisk **Dodaj**.

2. Zastąp definicję `Account` klasy z następującym kodem. Użyj definicje klas *właściwości zaimplementowane automatycznie*. Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Aby utworzyć `bankAccounts` lista, która zawiera dwa konta, Dodaj następujący kod do `ThisAddIn_Startup` method in Class metoda *ThisAddIn.vb* lub *ThisAddIn.cs*. Użyj deklaracji listy *inicjatory kolekcji*. Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Aby wyeksportować dane do programu Excel

1. W tym samym pliku Dodaj następującą metodę do `ThisAddIn` klasy. Metoda ustawia skoroszytu programu Excel i eksportuje dane do niego.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Dwie nowe funkcje języka C# są używane w przypadku tej metody. Obie te funkcje już istnieją w języku Visual Basic.

    - Metoda [Dodaj](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) ma *opcjonalny parametr* służącą do konkretnego szablonu. Parametry opcjonalne nowego w programie C# 4, umożliwiają pominięto argument dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument nie jest wysyłane w poprzednim przykładzie `Add` korzysta z domyślnego szablonu i utworzy nowy skoroszyt. Równoważne instrukcji we wcześniejszych wersjach języka C# wymaga argumentu symbolu zastępczego: `excelApp.Workbooks.Add(Type.Missing)`.

         Aby uzyskać więcej informacji, zobacz [nazwane i opcjonalne argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).

    - `Range` i `Offset` właściwości [zakres](<xref:Microsoft.Office.Interop.Excel.Range>) wykorzystują *właściwości indeksowanych* funkcji. Ta funkcja umożliwia korzystanie z tych właściwości z typów modelu COM za pomocą następujących typowych C# składni. Właściwości indeksowane również włączyć przy użyciu `Value` właściwość `Range` obiektu, eliminując konieczność stosowania `Value2` właściwości. `Value` Jest indeksowana właściwość, ale indeks jest opcjonalne. Argumenty opcjonalne właściwości indeksowanych współpracują w poniższym przykładzie.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         We wcześniejszych wersjach języka następującej specjalnej składni jest wymagana.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Nie można utworzyć właściwości indeksowanych samodzielnie. Ta funkcja obsługuje tylko użycie istniejącej właściwości indeksowanych.

         Aby uzyskać więcej informacji, zobacz [jak: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Dodaj następujący kod na końcu `DisplayInExcel` można dostosowywać szerokość kolumn w celu dopasowania do zawartości.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Te dodatki pokazują innej funkcji w języku C#: traktowanie `Object` zwracane z hostów COM, takich jak Office tak, jakby mają typu [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md). Jest to wykonywane automatycznie po **Osadź typy współdziałania** jest ustawiona na wartość domyślną `True`, lub ekwiwalentnie, gdy zestaw odwołuje się do niej [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) — opcja kompilatora. Typ `dynamic` umożliwia późnym wiązaniu już dostępna w języku Visual Basic i uniknięcie rzutowania jawnego, wymagane w C# 3.0 i wcześniejszych wersjach języka.

     Na przykład `excelApp.Columns[1]` zwraca `Object`, i `AutoFit` nadaje się program Excel [zakres](<xref:Microsoft.Office.Interop.Excel.Range>) metody. Bez `dynamic`, należy rzutować obiektu zwróconego przez `excelApp.Columns[1]` jako wystąpienie `Range` przed wywołaniem metody `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Aby uzyskać więcej informacji na temat osadzania typów międzyoperacyjnych Zobacz procedury "Aby znaleźć odwołania PIA" i "Aby przywrócić zależności PIA" w dalszej części tego tematu. Aby uzyskać więcej informacji na temat `dynamic`, zobacz [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md) lub [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Aby wywołać DisplayInExcel

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody. Wywołanie `DisplayInExcel` zawiera dwa argumenty. Pierwszy argument jest nazwa listy kont, które mają być przetwarzane. Drugi argument jest wyrażeniem lambda wielowierszowy, który definiuje, jak dane są do przetworzenia. `ID` i `balance` wartości dla każdego konta są wyświetlane w sąsiadujących komórek i wiersz jest wyświetlana na czerwono, jeśli saldo jest mniejsza niż zero. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Aby uruchomić program, naciśnij klawisz F5. Arkusz programu Excel pojawi się zawierającego dane z kont.

### <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metodę, aby utworzyć dokument programu Word, który zawiera łącze do skoroszytu programu Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Ten przykład demonstruje kilka nowych funkcji w języku C#: zdolność do pominięcia `ref` — słowo kluczowe w programowaniu modelu COM, argumenty nazwane i opcjonalne argumenty. Te funkcje są już istnieje w języku Visual Basic. [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) metoda zawiera siedem parametrów, które są zdefiniowane jako parametry opcjonalne informacje dodatkowe. Argumenty nazwane i opcjonalne pozwalają określić parametry, których chcesz uzyskać dostęp przez nazwę i wysyłać argumenty do tylko tych parametrów. W tym przykładzie argumenty są wysyłane do wskazania, że można utworzyć łącza do skoroszytu w Schowku (parametr `Link`) oraz że łącza, które ma być wyświetlana w dokumencie programu Word w postaci ikony (parametr `DisplayAsIcon`). Visual C# umożliwia również pominąć `ref` — słowo kluczowe dla tych argumentów.

### <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Naciśnij klawisz F5, aby uruchomić aplikację. Program Excel rozpoczyna się i wyświetla tabelę, który zawiera informacje z tych dwóch kont w `bankAccounts`. Pojawi się dokument programu Word zawierającego łącze do tabeli programu Excel.

### <a name="to-clean-up-the-completed-project"></a>Aby wyczyścić projektu ukończona

1. W programie Visual Studio, kliknij przycisk **czyste rozwiązanie** na **kompilacji** menu. W przeciwnym razie dodatek zostanie uruchomiony zawsze po otwarciu programu Excel na tym komputerze.

### <a name="to-find-the-pia-reference"></a>Aby znaleźć odwołania PIA

1. Uruchom ponownie aplikację, ale nie należy klikać przycisku **czyste rozwiązanie**.

2. Wybierz **Start**. Znajdź **programu Microsoft Visual Studio \<wersji >** , a następnie otwórz wiersz polecenia dla deweloperów.

3. Typ `ildasm` w wierszu polecenia dla deweloperów okna programu Visual Studio, a następnie naciśnij klawisz ENTER. Zostanie wyświetlone okno IL DASM.

4. Na **pliku** menu w oknie IL DASM, wybierz opcję **pliku** > **Otwórz**. Kliknij dwukrotnie **programu Visual Studio \<wersji >** , a następnie kliknij dwukrotnie **projektów**. Otwórz folder dla projektu i Znajdź folder bin/Debug *Nazwa projektu*.dll. Kliknij dwukrotnie *Nazwa projektu*.dll. Nowe okno wyświetla atrybuty projektu, oprócz odwołania do innych modułach i zestawach. Należy pamiętać, że przestrzenie nazw `Microsoft.Office.Interop.Excel` i `Microsoft.Office.Interop.Word` znajdują się w zestawie. Domyślnie w programie Visual Studio kompilator importuje typy, których potrzebujesz z odwołania PIA do swojego zestawu.

     Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie zawartości zestawu](../../../framework/app-domains/how-to-view-assembly-contents.md).

5. Kliknij dwukrotnie **MANIFESTU** ikony. Zostanie wyświetlone okno, który zawiera listę zestawów, które zawierają elementy przywoływanego przez projekt. `Microsoft.Office.Interop.Excel` i `Microsoft.Office.Interop.Word` nie są uwzględnione na liście. Ponieważ typy, które wymaga projektu zostały zaimportowane do swojego zestawu, odwołania do PIA nie są wymagane. Ułatwia to wdrożenie. Zestawy PIA nie muszą znajdować się na komputerze użytkownika, a ponieważ aplikacja nie wymaga wdrożenia określonej wersji podstawowy zestaw MIĘDZYOPERACYJNY, aplikacje można zaprojektować do pracy z wieloma wersjami pakietu Office, pod warunkiem, że niezbędne interfejsy API istnieje we wszystkich wersjach .

     Ponieważ Wdrażanie zestawów PIA nie jest już konieczne, można utworzyć aplikację w zaawansowanych scenariuszach, które współpracuje z wieloma wersjami pakietu Office, w tym wcześniejsze wersje. Jednak ta działa tylko wtedy, gdy kod nie używa żadnych interfejsów API, które nie są dostępne w wersji pakietu Office, w którym pracujesz. Nie zawsze jest jasne tego, czy określony interfejs API była dostępna w starszej wersji, a dla Przyczyna Praca z wcześniejszych wersji pakietu Office nie jest zalecane.

    > [!NOTE]
    > Pakiet Office nie opublikował zestawów PIA przed Office 2003. W związku z tym jedynym sposobem, aby wygenerować zestaw międzyoperacyjny dla pakietu Office w 2002 roku i jego wcześniejsze wersje jest importując odwołanie COM.

6. Zamknij okna manifestu i zestawu.

### <a name="to-restore-the-pia-dependency"></a>Aby przywrócić zależności PIA

1. W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku. Rozwiń **odwołania** i wybierz polecenie **Microsoft.Office.Interop.Excel**. Naciśnij klawisz F4, aby wyświetlić **właściwości** okna.

2. W **właściwości** oknie zmiany **Osadź typy współdziałania** właściwość **True** do **False**.

3. Powtórz kroki 1 i 2 w ramach tej procedury, aby uzyskać `Microsoft.Office.Interop.Word`.

4. W języku C#, przekształcić w komentarz dwóch wywołań do `Autofit` na końcu `DisplayInExcel` metody.

5. Naciśnij klawisz F5, aby zweryfikować, że projekt nadal działa poprawnie.

6. Powtórz kroki 1 – 3 poprzedniej procedury, aby otworzyć okno zestawu. Należy zauważyć, że `Microsoft.Office.Interop.Word` i `Microsoft.Office.Interop.Excel` nie są już na liście osadzone zespoły.

7. Kliknij dwukrotnie **MANIFESTU** ikonę i przewiń listę odwołania zestawów. Zarówno `Microsoft.Office.Interop.Word` i `Microsoft.Office.Interop.Excel` znajdują się na liście. Ponieważ aplikacja odwołuje się do programu Excel i Word zestawów PIA i **Osadź typy współdziałania** właściwość jest ustawiona na **False**, oba zestawy musi istnieć na komputerze użytkownika końcowego.

8. W programie Visual Studio, kliknij przycisk **czyste rozwiązanie** na **kompilacji** menu, aby wyczyścić projektu ukończona.

## <a name="see-also"></a>Zobacz także

- [Właściwości zaimplementowane automatycznie (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Właściwości zaimplementowane automatycznie (C#)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Wyrażenia lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda Expressions (C#)](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Instrukcje: Użycie właściwości indeksowanych w programowaniu usługi Międzyoperacyjnej modelu COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Przewodnik: Osadzanie typów z zarządzanych zestawów](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Współdziałanie](../../../csharp/programming-guide/interop/index.md)
