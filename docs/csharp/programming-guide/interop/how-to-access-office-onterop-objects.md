---
title: Jak uzyskać dostęp do obiektów międzyoperacyjności pakietu Office — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700838"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Jak uzyskać dostęp do obiektów międzyoperacyjności pakietu Office (C# Przewodnik programowania)

C#zawiera funkcje, które upraszczają dostęp do obiektów interfejsu API pakietu Office. Nowe funkcje obejmują argumenty nazwane i opcjonalne, nowy typ o nazwie `dynamic`i możliwość przekazywania argumentów do parametrów odwołań w metodach COM, tak jakby były parametrami wartości.

W tym temacie zostaną użyte nowe funkcje do napisania kodu, który tworzy i wyświetla Microsoft Office arkusz programu Excel. Następnie napiszesz kod, aby dodać dokument programu Office Word, który zawiera ikonę, która jest połączona z arkuszem programu Excel.

Aby ukończyć ten przewodnik, musisz mieć Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowszą wersję zainstalowanego na komputerze.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsolową

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**. **Nowy projekt** pojawi się okno dialogowe.

3. W okienku **zainstalowane szablony** rozwiń pozycję **Wizualizacja C#** , a następnie kliknij pozycję **Windows**.

4. Sprawdź u góry okna dialogowego **Nowy projekt** , aby upewnić się, że jako platforma docelowa została wybrana wersja **.NET Framework 4** (lub nowsza).

5. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.

6. Wpisz nazwę projektu w polu **Nazwa** .

7. Kliknij przycisk **OK**.

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

## <a name="to-add-references"></a>Aby dodać odwołania

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

2. Na stronie **zestawy** wybierz pozycję **Microsoft. Office. Interop. Word** na liście **Nazwa składnika** , a następnie przytrzymaj naciśnięty klawisz Ctrl i wybierz pozycję **Microsoft. Office. Interop. Excel**.  Jeśli zestawy nie są widoczne, może być konieczne zagwarantowanie, że są one zainstalowane i wyświetlane. Zobacz [jak: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Kliknij przycisk **OK**.

## <a name="to-add-necessary-using-directives"></a>Aby dodać wymagane dyrektywy using

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *program.cs* , a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące dyrektywy `using` na początku pliku kodu:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych

1. Wklej następującą definicję klasy do **program.cs**, w obszarze klasy `Program`.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Dodaj następujący kod do metody `Main` w celu utworzenia listy `bankAccounts` zawierającej dwa konta.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Aby zadeklarować metodę, która eksportuje informacje o koncie do programu Excel

1. Dodaj następującą metodę do klasy `Program`, aby skonfigurować arkusz programu Excel.

     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma opcjonalny parametr służący do określania określonego szablonu. Parametry opcjonalne, nowość w C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli ma być używana wartość domyślna parametru. Ponieważ żaden argument nie jest wysyłany w poniższym kodzie, `Add` używa szablonu domyślnego i tworzy nowy skoroszyt. Równoważna instrukcja we wcześniejszych wersjach programu C# wymaga argumentu symbolu zastępczego: `ExcelApp.Workbooks.Add(Type.Missing)`.

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. Dodaj następujący kod na końcu `DisplayInExcel`. Kod wstawia wartości do pierwszych dwóch kolumn pierwszego wiersza arkusza.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. Dodaj następujący kod na końcu `DisplayInExcel`. Pętla `foreach` umieszcza informacje z listy kont w pierwszych dwóch kolumnach arkusza.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Dodaj następujący kod na końcu `DisplayInExcel`, aby dopasować szerokości kolumn w celu dopasowania do zawartości.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Wcześniejsze wersje programu C# wymagają jawnego rzutowania tych operacji, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, a `AutoFit` to metoda <xref:Microsoft.Office.Interop.Excel.Range> programu Excel. W poniższych wierszach przedstawiono rzutowanie.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C#4 i nowsze wersje konwertuje zwracane `Object` do `dynamic` automatycznie, jeśli odwołanie do zestawu jest przywoływane przez opcję kompilatora [-link](../../language-reference/compiler-options/link-compiler-option.md) lub, równoważne, jeśli właściwość " **Osadź typy międzyoperacyjna** programu Excel" ma wartość true. Wartość true jest wartością domyślną dla tej właściwości.

## <a name="to-run-the-project"></a>Aby uruchomić projekt

1. Dodaj następujący wiersz na końcu `Main`.

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Naciśnij kombinację klawiszy CTRL + F5.

     Zostanie wyświetlony arkusz programu Excel zawierający dane z dwóch kont.

## <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word

1. Aby zilustrować dodatkowe sposoby, w których C# 4 i nowsze wersje rozszerzają Programowanie Office, poniższy kod otwiera aplikację Word i tworzy ikonę, która łączy się z arkuszem programu Excel.

     Wklej metodę `CreateIconInWordDoc`, która znajduje się w dalszej części tego kroku, do klasy `Program`. `CreateIconInWordDoc` używa argumentów nazwanych i opcjonalnych w celu zmniejszenia złożoności wywołań metod do <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> i <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Te wywołania obejmują dwie inne nowe funkcje wprowadzone w C# 4, które upraszczają wywołania metod com, które mają parametry referencyjne. Najpierw można wysłać argumenty do parametrów odwołania, tak jakby były one parametrami wartości. Oznacza to, że można wysyłać wartości bezpośrednio, bez tworzenia zmiennej dla każdego parametru odwołania. Kompilator generuje zmienne tymczasowe do przechowywania wartości argumentów i odrzuca zmienne po powrocie z wywołania. Następnie można pominąć słowo kluczowe `ref` na liście argumentów.

     Metoda `Add` ma cztery parametry referencyjne, z których wszystkie są opcjonalne. W C# 4,0 i nowszych wersjach można pominąć argumenty dla dowolnego lub wszystkich parametrów, jeśli chcesz użyć ich wartości domyślnych. W C# 3,0 i wcześniejszych wersjach argument musi być podany dla każdego parametru, a argument musi być zmienną, ponieważ parametry są parametrami odwołania.

     Metoda `PasteSpecial` Wstawia zawartość schowka. Metoda ma siedem parametrów referencyjnych, z których wszystkie są opcjonalne. Poniższy kod określa argumenty dla dwóch z nich: `Link`, aby utworzyć łącze do źródła zawartości Schowka, a `DisplayAsIcon`, aby wyświetlić łącze jako ikonę. W C# 4,0 i nowszych wersjach, można użyć nazwanych argumentów dla tych dwóch i pominąć pozostałe. Chociaż są to parametry odwołania, nie trzeba używać słowa kluczowego `ref` ani do tworzenia zmiennych, które mają być wysyłane jako argumenty. Można wysłać wartości bezpośrednio. W C# 3,0 i wcześniejszych wersjach, należy podać zmienną argumentu dla każdego parametru odwołania.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     W C# 3,0 i wcześniejszych wersjach języka wymagany jest Poniższy kod złożony.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. Dodaj następującą instrukcję na końcu `Main`.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. Dodaj następującą instrukcję na końcu `DisplayInExcel`. Metoda `Copy` dodaje arkusz do Schowka.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Naciśnij kombinację klawiszy CTRL + F5.

     Zostanie wyświetlony dokument programu Word zawierający ikonę. Kliknij dwukrotnie ikonę, aby przenieść arkusz na pierwszy plan.

## <a name="to-set-the-embed-interop-types-property"></a>Aby ustawić właściwość Osadź typy współdziałania

1. Dodatkowe ulepszenia są możliwe w przypadku wywołania typu COM, który nie wymaga podstawowego zestawu międzyoperacyjnego (PIA) w czasie wykonywania. Usunięcie zależności od zestawów Pia powoduje niezależność wersji i łatwiejsze wdrażanie. Aby uzyskać więcej informacji na temat korzyści z programowania bez zestawów Pia, zobacz [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md).

     Ponadto programowanie jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody modelu COM mogą być reprezentowane przy użyciu typu `dynamic`, a nie `Object`. Zmienne o typie `dynamic` nie są oceniane do czasu uruchomienia, co eliminuje konieczność jawnego rzutowania. Aby uzyskać więcej informacji, zobacz [Korzystanie z typu dynamicznego](../types/using-type-dynamic.md).

     W C# 4, osadzanie informacji o typie zamiast używania zestawów PIA jest zachowaniem domyślnym. Ze względu na to, że niektóre z powyższych przykładów są uproszczone, ponieważ jawne rzutowanie nie jest wymagane. Na przykład deklaracja `worksheet` w `DisplayInExcel` jest zapisywana jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` a nie `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Wywołania `AutoFit` w tej samej metodzie również wymagają jawnego rzutowania bez użycia domyślnego, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, a `AutoFit` jest metodą programu Excel. Poniższy kod przedstawia rzutowanie.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Aby zmienić wartość domyślną i użyć zestawów Pia zamiast osadzania informacji o typie, rozwiń węzeł **odwołania** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Microsoft. Office. Interop. Excel** lub **Microsoft. Office. Interop. Word**.

3. Jeśli nie widzisz okna **Właściwości** , naciśnij klawisz **F4**.

4. Znajdź **Osadź typy międzyoperacyjności** na liście właściwości i zmień jej wartość na **false**. Analogicznie, można skompilować przy użyciu opcji kompilatora [-Reference](../../language-reference/compiler-options/reference-compiler-option.md) zamiast [-link](../../language-reference/compiler-options/link-compiler-option.md) w wierszu polecenia.

## <a name="to-add-additional-formatting-to-the-table"></a>Aby dodać dodatkowe formatowanie do tabeli

1. Zastąp dwa wywołania `AutoFit` w `DisplayInExcel` z następującą instrukcją.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> ma siedem parametrów wartości, z których wszystkie są opcjonalne. Argumenty nazwane i opcjonalne umożliwiają podanie argumentów dla braku, niektórych lub wszystkich z nich. W poprzedniej instrukcji argument jest dostarczany tylko dla jednego z parametrów, `Format`. Ponieważ `Format` jest pierwszym parametrem na liście parametrów, nie trzeba podawać nazwy parametru. Jednak instrukcja może być łatwiejsza do zrozumienia, jeśli nazwa parametru jest uwzględniona, jak pokazano w poniższym kodzie.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Naciśnij klawisze CTRL + F5, aby zobaczyć wynik. Inne formaty są wymienione w wyliczeniu <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat>.

3. Porównaj instrukcję w kroku 1 z poniższym kodem, który pokazuje argumenty wymagane w C# 3,0 i wcześniejszych wersjach.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Przykład

Poniższy kod przedstawia kompletny przykład.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Jak używać argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
