---
title: 'Wskazówki: Programowanie Office (C# i Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 6c27442cb5c0c4172f503c945849e47560c2b33d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635356"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Wskazówki: Programowanie Office (C# i Visual Basic)

Program Visual Studio oferuje funkcje w językach C# i Visual Basic, które usprawniają programowanie pakietu Microsoft Office. Pomocne funkcje języka C# obejmują nazwane i `dynamic`opcjonalne argumenty oraz zwracane wartości typu . W programowaniu COM można pominąć `ref` słowo kluczowe i uzyskać dostęp do właściwości indeksowanych. Funkcje w języku Visual Basic obejmują właściwości implementowane automatycznie, instrukcje w wyrażeniach lambda i inicjatory kolekcji.

Oba języki umożliwiają osadzanie informacji o typie, co umożliwia wdrażanie zestawów, które współdziałają ze składnikami MODELU bez wdrażania podstawowych zestawów międzymiastowych (PIA) na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [Instruktaż: Osadzanie typów z zestawów zarządzanych](../../../standard/assembly/embed-types-visual-studio.md).

W tym instruktażeniu przedstawiono te funkcje w kontekście programowania pakietu Office, ale wiele z tych funkcji są również przydatne w programowaniu ogólnym. W instruktacie do utworzenia skoroszytu programu Excel za pomocą aplikacji dodatku programu Excel. Następnie należy utworzyć dokument programu Word zawierający łącze do skoroszytu. Na koniec zobaczysz, jak włączyć i wyłączyć zależność PIA.

## <a name="prerequisites"></a>Wymagania wstępne

Aby wypełnić ten instruktaż, na komputerze musi być zainstalowany program Microsoft Office Excel i program Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Aby skonfigurować aplikację dodatku programu Excel

1. Uruchom program Visual Studio.

2. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

3. W okienku **Zainstalowane szablony** rozwiń węzeł **Visual Basic** lub **Visual C#**, rozwiń **pakiet Office**, a następnie kliknij rok wersji produktu pakietu Office.

4. W okienku **Szablony** kliknij pozycję **Wersja programu Excel \<> dodatku**.

5. Spójrz na górze **szablonów** okienka, aby upewnić się, że **.NET Framework 4**, lub nowsza wersja, pojawia się w polu **Platforma docelowa.**

6. Wpisz nazwę projektu w polu **Nazwa,** jeśli chcesz.

7. Kliknij przycisk **OK**.

8. Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

### <a name="to-add-references"></a>Aby dodać odwołania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj odwołanie**. Pojawi się okno dialogowe **Dodawanie odwołania.**

2. Na karcie **Zestawy** wybierz pozycję **Microsoft.Office.Interop.Excel**, `<version>.0.0.0` wersja (dla klucza do numerów wersji produktu pakietu Office, zobacz [Wersje firmy Microsoft),](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)na liście Nazwa **składnika,** a następnie przytrzymaj naciśnięty klawisz CTRL i wybierz pozycję **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Jeśli nie widzisz zestawów, może być konieczne upewnienie się, że są one zainstalowane i wyświetlane (zobacz [Jak: Instalować podstawowe zestawy interop pakietu Office).](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)

3. Kliknij przycisk **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Aby dodać niezbędne instrukcje importowe lub za pomocą dyrektyw

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik **ThisAddIn.vb** lub **ThisAddIn.cs,** a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące `Imports` instrukcje (Visual `using` Basic) lub dyrektywy (C#) do górnej części pliku kodu, jeśli nie są jeszcze obecne.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Klasa**. Nazwij klasę Account.vb, jeśli używasz języka Visual Basic lub Account.cs, jeśli używasz języka C#. Kliknij przycisk **Dodaj**.

2. Zamień definicję `Account` klasy na następujący kod. Definicje klas używają *właściwości implementowanych automatycznie.* Aby uzyskać więcej informacji, zobacz [Właściwości implementowane automatycznie](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Aby utworzyć `bankAccounts` listę zawierającą dwa konta, dodaj `ThisAddIn_Startup` następujący kod do metody w *pliku ThisAddIn.vb* lub *ThisAddIn.cs*. Deklaracje listy używają *inicjatorów kolekcji*. Aby uzyskać więcej informacji, zobacz [Inicjowanie kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Aby wyeksportować dane do programu Excel

1. W tym samym pliku dodaj następującą metodę do `ThisAddIn` klasy. Metoda konfigurowała skoroszyt programu Excel i eksportuje do niego dane.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Dwie nowe funkcje języka C# są używane w tej metodzie. Obie te funkcje już istnieją w języku Visual Basic.

    - Metoda [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) ma *opcjonalny parametr* określający określony szablon. Parametry opcjonalne, nowe w języku C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument nie jest `Add` wysyłany w poprzednim przykładzie, używa szablonu domyślnego i tworzy nowy skoroszyt. Równoważna instrukcja we wcześniejszych wersjach języka `excelApp.Workbooks.Add(Type.Missing)`C# wymaga argumentu zastępczego: .

         Aby uzyskać więcej informacji, zobacz [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md).

    - Właściwości `Range` `Offset` i właściwości [Range](<xref:Microsoft.Office.Interop.Excel.Range>) obiektu używają funkcji *właściwości indeksowanych.* Ta funkcja umożliwia korzystanie z tych właściwości z typów COM przy użyciu następujących typowych składni C#. Właściwości indeksowane umożliwiają również korzystanie `Value` z `Range` właściwości obiektu, eliminując `Value2` konieczność korzystania z właściwości. Właściwość `Value` jest indeksowana, ale indeks jest opcjonalny. Opcjonalne argumenty i właściwości indeksowane współpracują ze sobą w poniższym przykładzie.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         We wcześniejszych wersjach języka wymagana jest następująca specjalna składnia.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Nie można tworzyć właściwości indeksowanych własnych. Funkcja obsługuje tylko zużycie istniejących właściwości indeksowanych.

         Aby uzyskać więcej informacji, zobacz [Jak używać właściwości indeksowanych w programowaniu współdziałania COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Dodaj następujący kod na `DisplayInExcel` końcu, aby dostosować szerokość kolumn, aby dopasować ją do zawartości.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Te dodatki pokazują inną funkcję w `Object` języku C#: traktowanie wartości zwracanych z hostów COM, takich jak Office, tak jakby miały typ [dynamiczny](../../language-reference/builtin-types/reference-types.md). Dzieje się tak automatycznie, gdy **embed Interop** `True`Types jest ustawiona na jego wartość domyślną, lub, podobnie, gdy zestaw odwołuje się do opcji [kompilatora -link.](../../language-reference/compiler-options/link-compiler-option.md) Type `dynamic` umożliwia późne wiązanie, już dostępne w języku Visual Basic i unika jawnego rzutowania wymaganego w języku C# 3.0 i wcześniejszych wersjach języka.

     Na przykład `excelApp.Columns[1]` zwraca `Object`, `AutoFit` i jest excel [Zakres](<xref:Microsoft.Office.Interop.Excel.Range>) metody. Bez `dynamic`, należy oddać obiekt `excelApp.Columns[1]` zwrócony `Range` przez jako `AutoFit`wystąpienie przed wywołaniem metody .

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Aby uzyskać więcej informacji na temat osadzania typów współdziałania, zobacz procedury "Aby znaleźć odwołanie pia" i "Aby przywrócić zależność PIA" w dalszej części tego tematu. Aby uzyskać `dynamic`więcej informacji na temat , zobacz [dynamiczny](../../language-reference/builtin-types/reference-types.md) lub [Korzystanie z funkcji Typ dynamiczny](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Aby wywołać DisplayInExcel

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody. Wywołanie `DisplayInExcel` zawiera dwa argumenty. Pierwszy argument to nazwa listy kont do przetworzenia. Drugi argument jest wielowierszowe wyrażenie lambda, który definiuje, jak dane mają być przetwarzane. Wartości `ID` `balance` i dla każdego konta są wyświetlane w sąsiednich komórkach, a wiersz jest wyświetlany na czerwono, jeśli saldo jest mniejsze niż zero. Aby uzyskać więcej informacji, zobacz [Wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Aby uruchomić program, naciśnij klawisz F5. Pojawi się arkusz programu Excel zawierający dane z kont.

### <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word

1. Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody, aby utworzyć dokument programu Word zawierający łącze do skoroszytu programu Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Ten kod demonstruje kilka nowych funkcji w języku `ref` C#: możliwość pominięcia słowa kluczowego w programowaniu COM, nazwane argumenty i argumenty opcjonalne. Te funkcje już istnieją w języku Visual Basic. [Metoda WklejanieSpecjalne](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) ma siedem parametrów, z których wszystkie są zdefiniowane jako opcjonalne parametry referencyjne. Nazwane i opcjonalne argumenty umożliwiają wyznaczenie parametrów, do których chcesz uzyskać dostęp według nazwy, i wysyłanie argumentów tylko do tych parametrów. W tym przykładzie argumenty są wysyłane, aby wskazać, że łącze do skoroszytu w Schowku powinno zostać utworzone (parametr) `Link`i że łącze ma być wyświetlane w dokumencie programu Word jako ikona (parametr). `DisplayAsIcon` Visual C# umożliwia również pominąć `ref` słowo kluczowe dla tych argumentów.

### <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Naciśnij klawisz F5, aby uruchomić aplikację. Program Excel uruchamia i wyświetla tabelę zawierającą `bankAccounts`informacje z dwóch kont w programie . Następnie zostanie wyświetlony dokument programu Word zawierający łącze do tabeli programu Excel.

### <a name="to-clean-up-the-completed-project"></a>Aby oczyścić ukończony projekt

1. W programie Visual Studio kliknij pozycję **Wyczyść rozwiązanie** w menu **Kompilacja.** W przeciwnym razie dodatek będzie uruchamiany przy każdym otwarciu programu Excel na komputerze.

### <a name="to-find-the-pia-reference"></a>Aby znaleźć odwołanie pia

1. Uruchom aplikację ponownie, ale nie klikaj przycisku **Wyczyść rozwiązanie**.

2. Wybierz **pozycję Start**. Znajdź **wersję \<programu Microsoft Visual Studio>** i otwórz wiersz polecenia dewelopera.

3. Wpisz `ildasm` w wierszu polecenia dewelopera dla programu Visual Studio, a następnie naciśnij klawisz ENTER. Zostanie wyświetlone okno IL DASM.

4. W menu **Plik** w oknie IL DASM wybierz **pozycję Otwórz plik** > **Open**. Kliknij dwukrotnie **>\<wersji programu Visual Studio, **a następnie kliknij dwukrotnie pozycję **Projekty**. Otwórz folder projektu i poszukaj w folderze bin/debugdla *nazwy projektu*.dll. Kliknij dwukrotnie *nazwę projektu*.dll. Nowe okno wyświetla atrybuty projektu, oprócz odwołań do innych modułów i zestawów. Należy zauważyć, `Microsoft.Office.Interop.Excel` `Microsoft.Office.Interop.Word` że obszary nazw i są zawarte w zestawie. Domyślnie w programie Visual Studio kompilator importuje potrzebne typy z identyfikatora PIA, do którego istnieje odwołanie, do zestawu.

     Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie zawartości zestawu](../../../standard/assembly/view-contents.md).

5. Kliknij dwukrotnie ikonę **MANIFEST.** Zostanie wyświetlone okno zawierające listę zestawów zawierających elementy, do których odwołuje się projekt. `Microsoft.Office.Interop.Excel`i `Microsoft.Office.Interop.Word` nie są ujęte na liście. Ponieważ typy, których potrzeby projektu zostały zaimportowane do zestawu, odwołania do pia nie są wymagane. Ułatwia to wdrażanie. PiAs nie muszą być obecne na komputerze użytkownika, a ponieważ aplikacja nie wymaga wdrożenia określonej wersji pia, aplikacje mogą być zaprojektowane do pracy z wieloma wersjami pakietu Office, pod warunkiem, że niezbędne interfejsy API istnieją we wszystkich wersjach .

     Ponieważ wdrażanie pias nie jest już konieczne, można utworzyć aplikację w zaawansowanych scenariuszach, która działa z wieloma wersjami pakietu Office, w tym wcześniejszych wersji. Jednak to działa tylko wtedy, gdy kod nie używa żadnych interfejsów API, które nie są dostępne w wersji pakietu Office, z którą pracujesz. Nie zawsze jest jasne, czy określony interfejs API był dostępny we wcześniejszej wersji i z tego powodu nie jest zalecane działanie z wcześniejszymi wersjami pakietu Office.

    > [!NOTE]
    > Office nie opublikował pias przed pakietem Office 2003. W związku z tym jedynym sposobem wygenerowania zestawu współdwywanego dla pakietu Office 2002 lub wcześniejszych wersji jest importowanie odwołania COM.

6. Zamknij okno manifestu i okno złożenia.

### <a name="to-restore-the-pia-dependency"></a>Aby przywrócić zależność PIA

1. W **Eksploratorze rozwiązań**kliknij przycisk **Pokaż wszystkie pliki.** Rozwiń folder **Odwołania** i wybierz pozycję **Microsoft.Office.Interop.Excel**. Naciśnij klawisz F4, aby wyświetlić okno **Właściwości.**

2. W oknie **Właściwości** zmień właściwość **Embed Interop Types** z **True** na **False**.

3. Powtórz kroki 1 i 2 `Microsoft.Office.Interop.Word`w tej procedurze dla .

4. W języku C#, skomentować `Autofit` dwa `DisplayInExcel` wywołania na końcu metody.

5. Naciśnij klawisz F5, aby sprawdzić, czy projekt nadal działa poprawnie.

6. Powtórz kroki 1-3 z poprzedniej procedury, aby otworzyć okno złożenia. Należy `Microsoft.Office.Interop.Word` zauważyć, że i `Microsoft.Office.Interop.Excel` nie są już na liście zestawów osadzonych.

7. Kliknij dwukrotnie ikonę **MANIFEST** i przewiń listę zestawów, do których istnieje odwołanie. Oba `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` i są na liście. Ponieważ aplikacja odwołuje się do pias excel i word, a **embed Typy międzyop** jest ustawiona na **False**, oba zestawy muszą istnieć na komputerze użytkownika końcowego.

8. W programie Visual Studio kliknij pozycję **Wyczyść rozwiązanie** w menu **Kompilacja,** aby oczyścić ukończony projekt.

## <a name="see-also"></a>Zobacz też

- [Właściwości zaimplementowane automatycznie (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Właściwości implementowane automatycznie (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)
- [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Wczesne i późne wiązanie](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dynamiczne](../../language-reference/builtin-types/reference-types.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Lambda — Wyrażenia (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Wyrażenia Lambda (C#)](../statements-expressions-operators/lambda-expressions.md)
- [Używanie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md)
- [Przewodnik: Tworzenie pierwszego dodatku VSTO dla programu Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Współdziałanie](./index.md)
