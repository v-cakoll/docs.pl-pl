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
ms.openlocfilehash: 8ed6e759f682f0db76938661fdcf668bec1eef1c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588970"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Przewodnik: Programowanie Office (C# i Visual Basic)

Program Visual Studio oferuje funkcje C# programu i Visual Basic, które zwiększają Microsoft Office programowanie. Przydatne C# funkcje obejmują argumenty nazwane i opcjonalne oraz zwracane wartości typu `dynamic`. W programowaniu com można pominąć `ref` słowo kluczowe i uzyskać dostęp do właściwości indeksowanych. Funkcje w Visual Basic zawierają właściwości, które są implementowane przez funkcję autouzupełniania, instrukcje w wyrażeniach lambda i Inicjatory kolekcji.

Oba języki umożliwiają osadzanie informacji o typie, dzięki czemu można wdrażać zestawy, które współdziałają ze składnikami modelu COM bez wdrażania podstawowych zestawów międzyoperacyjnych (zestawów PIA) na komputerze użytkownika. Aby uzyskać więcej informacji, [zobacz Przewodnik: Osadzanie typów z zarządzanych zestawów](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).

W tym instruktażu przedstawiono te funkcje w kontekście programowania pakietu Office, ale wiele z tych funkcji jest również przydatnych w programowaniu ogólnym. W tym przewodniku używasz aplikacji dodatku programu Excel do tworzenia skoroszytu programu Excel. Następnie utworzysz dokument programu Word zawierający link do skoroszytu. Na koniec zobaczysz, jak włączyć i wyłączyć zależność PIA.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć zainstalowany Microsoft Office Excel i Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Aby skonfigurować aplikację dodatku dla programu Excel

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku **zainstalowane szablony** rozwiń węzeł **Visual Basic** lub **Wizualizacja C#** , rozwiń węzeł **Office**, a następnie kliknij pozycję wersja roku produktu pakietu Office.

4. W okienku **Szablony** kliknij pozycję **Excel \<wersja > dodatek**.

5. Sprawdź górną część okienka **Szablony** , aby upewnić się, że w polu **platforma** docelowa zostanie wyświetlona **.NET Framework 4**lub nowsza wersja.

6. Jeśli chcesz, wpisz nazwę projektu w polu **Nazwa** .

7. Kliknij przycisk **OK**.

8. Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

### <a name="to-add-references"></a>Aby dodać odwołania

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

2. Na karcie **zestawy** wybierz pozycję **Microsoft. Office. Interop. Excel**, wersję `<version>.0.0.0` (dla klucza w numerach wersji produktu pakietu Office, zobacz [Microsoft Versions](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), na liście **Nazwa składnika** , a następnie naciśnij klawisz Ctrl. i wybierz **Microsoft. Office. Interop. Word**, `version <version>.0.0.0`. Jeśli zestawy nie są widoczne, może być konieczne zagwarantowanie, że są one zainstalowane i wyświetlone ( [zobacz How to: Zainstaluj podstawowe zestawy](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)międzyoperacyjności pakietu Office.

3. Kliknij przycisk **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Aby dodać wymagane instrukcje importu lub dyrektywy

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik **ThisAddIn. vb** lub **ThisAddIn.cs** , a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące `Imports` instrukcje (Visual Basic) lub `using` dyrektywy (C#) na górze pliku kodu, jeśli jeszcze nie istnieją.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Klasa**. Nadaj nazwę klasy Account. vb, jeśli używasz programu Visual Basic lub Account.cs C#. Kliknij przycisk **Dodaj**.

2. Zastąp definicję `Account` klasy następującym kodem. Definicje klas używają *Właściwości*, które są implementowane. Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Aby utworzyć `bankAccounts` listę zawierającą dwa konta, Dodaj następujący kod `ThisAddIn_Startup` do metody w *ThisAddIn. vb* lub *ThisAddIn.cs*. Deklaracje list używają *inicjatorów kolekcji*. Aby uzyskać więcej informacji, zobacz [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Aby wyeksportować dane do programu Excel

1. W tym samym pliku Dodaj następującą metodę do `ThisAddIn` klasy. Metoda konfiguruje skoroszyt programu Excel i eksportuje do niego dane.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     W tej C# metodzie są używane dwie nowe funkcje. Obie te funkcje już istnieją w Visual Basic.

    - Metoda [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) ma *opcjonalny parametr* służący do określania określonego szablonu. Parametry opcjonalne, nowość w C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli ma być używana wartość domyślna parametru. Ponieważ żaden argument nie jest wysyłany w poprzednim przykładzie `Add` , używa szablonu domyślnego i tworzy nowy skoroszyt. Równoważna instrukcja we wcześniejszych wersjach programu C# wymaga argumentu symbolu zastępczego `excelApp.Workbooks.Add(Type.Missing)`:.

         Aby uzyskać więcej informacji, zobacz [argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md).

    - Właściwości `Range` i `Offset` obiektu [Range](<xref:Microsoft.Office.Interop.Excel.Range>) używają funkcji *indeksowanych właściwości* . Ta funkcja umożliwia korzystanie z tych właściwości z typów COM przy użyciu następującej składni typowej C# . Właściwości indeksowane umożliwiają również korzystanie `Value` z właściwości `Range` obiektu, eliminując konieczność używania `Value2` właściwości. `Value` Właściwość jest indeksowana, ale indeks jest opcjonalny. Argumenty opcjonalne i właściwości indeksowane działają razem w poniższym przykładzie.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         W starszych wersjach języka wymagana jest następująca specjalna składnia.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Nie można tworzyć własnych właściwości indeksowanych. Funkcja obsługuje tylko użycie istniejących właściwości indeksowanych.

         Aby uzyskać więcej informacji, zobacz [jak: Użyj właściwości indeksowanych w programowaniu](./how-to-use-indexed-properties-in-com-interop-rogramming.md)międzyoperacyjnym modelu com.

2. Dodaj następujący kod na końcu `DisplayInExcel` , aby dostosować szerokości kolumn w celu dopasowania do zawartości.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Te dodatki przedstawiają kolejną funkcję C#w: `Object` traktowanie wartości zwracanych z hostów com, takich jak pakiet Office, tak jakby były typu [dynamicznego](../../language-reference/keywords/dynamic.md). Dzieje się tak automatycznie, gdy **osadzanie typów** międzyoperacyjnych jest ustawione `True`na wartość domyślną, lub, równoważne, gdy zestaw jest przywoływany przez opcję kompilatora [/link](../../language-reference/compiler-options/link-compiler-option.md) . Typ `dynamic` umożliwia późne wiązanie, już dostępne w Visual Basic i pozwala uniknąć jawnego rzutowania wymaganego w C# 3,0 i wcześniejszych wersjach języka.

     Na przykład `excelApp.Columns[1]` `AutoFit` zwraca, i jest metodą zakresu programu Excel. [](<xref:Microsoft.Office.Interop.Excel.Range>) `Object` Bez `dynamic`, należy rzutować obiekt zwracany przez `excelApp.Columns[1]` wystąpienie `Range` przed wywołaniem metody `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Aby uzyskać więcej informacji na temat osadzania typów międzyoperacyjnych, zobacz procedury "aby znaleźć odwołanie PIA" i "aby przywrócić zależność PIA" w dalszej części tego tematu. Aby uzyskać więcej informacji `dynamic`na temat, zobacz [dynamiczne](../../language-reference/keywords/dynamic.md) lub [Używanie typu dynamicznego](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Aby wywołać DisplayInExcel

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody. Wywołanie `DisplayInExcel` zawiera dwa argumenty. Pierwszy argument to nazwa listy kont do przetworzenia. Drugi argument jest wielowierszowym wyrażeniem lambda, które definiuje sposób przetwarzania danych. Wartości `ID` i`balance` dla każdego konta są wyświetlane w sąsiednich komórkach, a wiersz jest wyświetlany na czerwono, jeśli saldo jest mniejsze od zera. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Aby uruchomić program, naciśnij klawisz F5. Zostanie wyświetlony arkusz programu Excel zawierający dane z kont.

### <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody, aby utworzyć dokument programu Word, który zawiera link do skoroszytu programu Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Ten kod ilustruje kilka nowych funkcji w C#: możliwość pomijania `ref` słowa kluczowego w programowaniu com, argumentach nazwanych i opcjonalnych argumentach. Te funkcje już istnieją w Visual Basic. Metoda [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) ma siedem parametrów, spośród których wszystkie są zdefiniowane jako opcjonalne parametry odwołania. Argumenty nazwane i opcjonalne umożliwiają określenie parametrów, do których chcesz uzyskać dostęp według nazwy, i wysłanie argumentów tylko do tych parametrów. W tym przykładzie argumenty są wysyłane w celu wskazania, że należy utworzyć link do skoroszytu w schowku (parametr `Link`) i czy łącze ma być wyświetlane w dokumencie programu Word jako ikona (parametr `DisplayAsIcon`). Wizualizacja C# umożliwia również pominięcie `ref` słowa kluczowego dla tych argumentów.

### <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Naciśnij klawisz F5, aby uruchomić aplikację. Program Excel zostanie uruchomiony i wyświetli tabelę zawierającą informacje z dwóch kont w `bankAccounts`. Zostanie wyświetlony dokument programu Word zawierający link do tabeli programu Excel.

### <a name="to-clean-up-the-completed-project"></a>Aby wyczyścić ukończony projekt

1. W programie Visual Studio kliknij pozycję **Wyczyść rozwiązanie** w menu **kompilacja** . W przeciwnym razie dodatek będzie uruchamiany za każdym razem, gdy otworzysz program Excel na komputerze.

### <a name="to-find-the-pia-reference"></a>Aby znaleźć odwołanie PIA

1. Uruchom aplikację ponownie, ale nie klikaj przycisku **Wyczyść rozwiązanie**.

2. Wybierz pozycję **Rozpocznij**. Znajdź **Microsoft Visual Studio \<wersji >** i Otwórz wiersz polecenia dewelopera.

3. Wpisz `ildasm` w oknie wiersz polecenia dla deweloperów dla programu Visual Studio, a następnie naciśnij klawisz ENTER. Zostanie wyświetlone okno IL DASM.

4. W menu **plik** w oknie Il DASM wybierz pozycję **plik** > **Otwórz**. Kliknij dwukrotnie **program Visual Studio \<w wersji >** , a następnie kliknij dwukrotnie pozycję **projekty**. Otwórz folder dla projektu i sprawdź folder bin/debug dla *nazwy projektu*. dll. Kliknij dwukrotnie *nazwę projektu*. dll. Nowe okno wyświetla atrybuty projektu, oprócz odwołań do innych modułów i zestawów. Należy zauważyć, `Microsoft.Office.Interop.Excel` że `Microsoft.Office.Interop.Word` przestrzenie nazw i znajdują się w zestawie. Domyślnie w programie Visual Studio kompilator importuje wymagane typy z przywoływanego PIA do zestawu.

     Aby uzyskać więcej informacji, zobacz [jak: Wyświetl zawartość](../../../framework/app-domains/how-to-view-assembly-contents.md)zestawu.

5. Kliknij dwukrotnie ikonę **manifestu** . Zostanie wyświetlone okno zawierające listę zestawów zawierających elementy, do których odwołuje się projekt. `Microsoft.Office.Interop.Excel`i `Microsoft.Office.Interop.Word` nie znajdują się na liście. Ponieważ typy wymagane przez projekt zostały zaimportowane do zestawu, odwołania do PIA nie są wymagane. Ułatwia to wdrażanie. Zestawów PIA nie muszą znajdować się na komputerze użytkownika, a ponieważ aplikacja nie wymaga wdrożenia określonej wersji PIA, aplikacje mogą być zaprojektowane do pracy z wieloma wersjami pakietu Office, pod warunkiem, że niezbędne interfejsy API istnieją we wszystkich wersjach .

     Ponieważ wdrożenie zestawów PIA nie jest już konieczne, można utworzyć aplikację w zaawansowanych scenariuszach, które współdziałają z wieloma wersjami pakietu Office, w tym z wcześniejszymi wersjami. Jednak jest to możliwe tylko wtedy, gdy kod nie używa żadnych interfejsów API, które nie są dostępne w używanej wersji pakietu Office. Nie zawsze należy czyścić, czy określony interfejs API jest dostępny w starszej wersji, a z tego powodu nie zaleca się korzystania z wcześniejszych wersji pakietu Office.

    > [!NOTE]
    > Pakiet Office nie opublikował zestawów Pia przed pakietem Office 2003. W związku z tym jedynym sposobem na wygenerowanie zestawu międzyoperacyjnego dla pakietu Office 2002 lub wcześniejszych wersji jest zaimportowanie odwołania COM.

6. Zamknij okno manifestu i okno zestawu.

### <a name="to-restore-the-pia-dependency"></a>Aby przywrócić zależność PIA

1. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** . Rozwiń folder **odwołania** i wybierz pozycję **Microsoft. Office. Interop. Excel**. Naciśnij klawisz F4, aby wyświetlić okno **Właściwości** .

2. W oknie **Właściwości** Zmień właściwość **Osadź typy** współdziałania z **true** na **false**.

3. Powtórz kroki 1 i 2 w tej procedurze dla `Microsoft.Office.Interop.Word`programu.

4. W C#programie Dodaj komentarz do `Autofit` dwóch wywołań na końcu `DisplayInExcel` metody.

5. Naciśnij klawisz F5, aby sprawdzić, czy projekt nadal działa poprawnie.

6. Powtórz kroki 1-3 z poprzedniej procedury, aby otworzyć okno zestawu. Zwróć uwagę `Microsoft.Office.Interop.Word` , `Microsoft.Office.Interop.Excel` że nie znajdują się już na liście osadzonych zestawów.

7. Kliknij dwukrotnie ikonę **manifestu** i przewiń listę przywoływanych zestawów. Obie `Microsoft.Office.Interop.Word` i`Microsoft.Office.Interop.Excel` znajdują się na liście. Ponieważ aplikacja odwołuje się do programów Excel i Word zestawów Pia, a właściwość **Osadź typy** międzyoperacyjna ma wartość **false**, oba zestawy muszą istnieć na komputerze użytkownika końcowego.

8. W programie Visual Studio kliknij pozycję **Wyczyść rozwiązanie** w menu **kompilacja** , aby wyczyścić ukończony projekt.

## <a name="see-also"></a>Zobacz także

- [Właściwości zaimplementowane przez funkcję autoimplementacji (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Właściwości zaimplementowane przez funkcję (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)
- [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Wyrażenia lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda Expressions (C#)](../statements-expressions-operators/lambda-expressions.md)
- [Instrukcje: Korzystanie z właściwości indeksowanych w programowaniu międzyoperacyjnym modelu COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Przewodnik: Osadzanie typów z zarządzanych zestawów](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Współdziałanie](./index.md)
