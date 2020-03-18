---
title: Jak uzyskać dostęp do obiektów pakietu Office interop - Przewodnik programowania C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700838"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Jak uzyskać dostęp do obiektów pakietu Office interop (Przewodnik programowania Języka C#)

Język C# ma funkcje, które upraszczają dostęp do obiektów interfejsu API pakietu Office. Nowe funkcje obejmują nazwane i opcjonalne `dynamic`argumenty, nowy typ o nazwie i możliwość przekazywania argumentów do parametrów referencyjnych w metodach COM, tak jakby były parametrami wartości.

W tym temacie użyjesz nowych funkcji do pisania kodu, który tworzy i wyświetla arkusz programu Microsoft Office Excel. Następnie napiszesz kod, aby dodać dokument programu Office Word zawierający ikonę połączoną z arkuszem programu Excel.

Aby wypełnić ten instruktaż, na komputerze muszą być zainstalowane programy Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowsze wersje.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli

1. Uruchom program Visual Studio.

2. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**. Zostanie wyświetlone okno dialogowe **Nowy projekt**.

3. W okienku **Zainstalowane szablony** rozwiń węzeł **Visual C#,** a następnie kliknij pozycję **Windows**.

4. Spójrz na górze okna dialogowego **Nowy projekt,** aby upewnić się, że **.NET Framework 4** (lub nowsza wersja) jest wybrany jako platforma docelowa.

5. W okienku **Szablony** kliknij pozycję **Aplikacja konsoli**.

6. Wpisz nazwę projektu w polu **Nazwa.**

7. Kliknij przycisk **OK**.

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

## <a name="to-add-references"></a>Aby dodać odwołania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj odwołanie**. Pojawi się okno dialogowe **Dodawanie odwołania.**

2. Na stronie **Zestawy** wybierz pozycję **Microsoft.Office.Interop.Word** na liście **Nazwa składnika,** a następnie przytrzymaj naciśnięty klawisz CTRL i wybierz pozycję **Microsoft.Office.Interop.Excel**.  Jeśli nie widzisz zestawów, może być konieczne upewnienie się, że są one zainstalowane i wyświetlane. Zobacz [jak: Instalowanie podstawowych zestawów interop pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. Kliknij przycisk **OK**.

## <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne za pomocą dyrektyw

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Program.cs,* a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące `using` dyrektywy do górnej części pliku kodu:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych

1. Wklej następującą **Program.cs**definicję klasy `Program` do Program.cs , w klasie.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. Dodaj następujący kod `Main` do metody, `bankAccounts` aby utworzyć listę zawierającą dwa konta.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Aby zadeklarować metodę eksportuzią informacje o koncie do programu Excel

1. Dodaj następującą `Program` metodę do klasy, aby skonfigurować arkusz programu Excel.

     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma opcjonalny parametr do określania określonego szablonu. Parametry opcjonalne, nowe w języku C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument nie jest `Add` wysyłany w następującym kodzie, używa szablonu domyślnego i tworzy nowy skoroszyt. Równoważna instrukcja we wcześniejszych wersjach języka `ExcelApp.Workbooks.Add(Type.Missing)`C# wymaga argumentu zastępczego: .

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. Dodaj następujący kod na `DisplayInExcel`końcu pliku . Kod wstawia wartości do pierwszych dwóch kolumn pierwszego wiersza arkusza.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. Dodaj następujący kod na `DisplayInExcel`końcu pliku . Pętla `foreach` umieszcza informacje z listy kont w pierwszych dwóch kolumnach kolejnych wierszy arkusza.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Dodaj następujący kod na `DisplayInExcel` końcu, aby dostosować szerokość kolumn, aby dopasować ją do zawartości.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Wcześniejsze wersje języka C# wymagają jawnego `Object`rzutowania `AutoFit` dla <xref:Microsoft.Office.Interop.Excel.Range> tych operacji, ponieważ `ExcelApp.Columns[1]` zwraca metodę programu Excel i jest metodą programu Excel. W poniższych wierszach przedstawiono rzutowanie.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C# 4 i nowsze wersje `Object` `dynamic` konwertuje zwracane do automatycznie, jeśli zestaw odwołuje się do opcji kompilatora [-link](../../language-reference/compiler-options/link-compiler-option.md) lub, podobnie, jeśli program Excel **Embed Interop Types** właściwość jest ustawiona na true. Wartość True jest wartością domyślną dla tej właściwości.

## <a name="to-run-the-project"></a>Aby uruchomić projekt

1. Dodaj następujący wiersz na `Main`końcu .

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. Naciśnij klawisze CTRL+F5.

     Pojawi się arkusz programu Excel zawierający dane z dwóch kont.

## <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word

1. Aby zilustrować dodatkowe sposoby, w których C# 4 i nowsze wersje, zwiększa programowanie pakietu Office, poniższy kod otwiera aplikację programu Word i tworzy ikonę, która łączy się z arkuszem programu Excel.

     Wklej `CreateIconInWordDoc`metodę , pod warunkiem, `Program` że w dalszej części tego kroku, do klasy. `CreateIconInWordDoc`używa nazwanych i opcjonalnych argumentów, aby <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>zmniejszyć złożoność wywołań metody i . Te wywołania zawierają dwie inne nowe funkcje wprowadzone w języku C# 4, które upraszczają wywołania metod COM, które mają parametry referencyjne. Najpierw można wysyłać argumenty do parametrów odwołania tak, jakby były parametrami wartości. Oznacza to, że można wysyłać wartości bezpośrednio, bez tworzenia zmiennej dla każdego parametru odwołania. Kompilator generuje zmienne tymczasowe do przechowywania wartości argumentu i odrzuca zmienne po powrocie z wywołania. Po drugie, można `ref` pominąć słowo kluczowe na liście argumentów.

     Metoda `Add` ma cztery parametry referencyjne, z których wszystkie są opcjonalne. W wersji C# 4.0 i nowszych można pominąć argumenty dla dowolnego lub wszystkich parametrów, jeśli chcesz użyć ich wartości domyślnych. W języku C# 3.0 i wcześniejszych wersjach należy podać argument dla każdego parametru, a argument musi być zmienna, ponieważ parametry są parametrami referencyjnymi.

     Metoda `PasteSpecial` wstawia zawartość Schowka. Metoda ma siedem parametrów referencyjnych, z których wszystkie są opcjonalne. Poniższy kod określa argumenty dla `Link`dwóch z nich: , aby utworzyć łącze do `DisplayAsIcon`źródła zawartości Schowka i , aby wyświetlić łącze jako ikonę. W wersji C# 4.0 i nowszych można użyć nazwanych argumentów dla tych dwóch i pominąć inne. Chociaż są to parametry referencyjne, nie `ref` trzeba używać słowa kluczowego ani tworzyć zmiennych do wysyłania jako argumentów. Wartości można wysyłać bezpośrednio. W języku C# 3.0 i wcześniejszych wersjach należy podać argument zmiennej dla każdego parametru odwołania.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     W języku C# 3.0 i wcześniejszych wersjach języka wymagany jest następujący bardziej złożony kod.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. Dodaj następującą instrukcję `Main`na końcu .

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. Dodaj następującą instrukcję `DisplayInExcel`na końcu . Metoda `Copy` dodaje arkusz do Schowka.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. Naciśnij klawisze CTRL+F5.

     Zostanie wyświetlony dokument programu Word zawierający ikonę. Kliknij dwukrotnie ikonę, aby przenieść arkusz na pierwszy plan.

## <a name="to-set-the-embed-interop-types-property"></a>Aby ustawić właściwość Embed Interop Types

1. Dodatkowe ulepszenia są możliwe podczas wywoływania typu COM, który nie wymaga podstawowego zestawu współrzędnego (PIA) w czasie wykonywania. Usunięcie zależności od pias powoduje niezależność wersji i łatwiejsze wdrażanie. Aby uzyskać więcej informacji na temat zalet programowania bez pias, zobacz [Instruktaż: Osadzanie typów z zestawów zarządzanych](../../../standard/assembly/embed-types-visual-studio.md).

     Ponadto programowanie jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody `dynamic` COM `Object`mogą być reprezentowane przy użyciu typu zamiast . Zmienne, które `dynamic` mają typ nie są oceniane do czasu wykonywania, co eliminuje potrzebę jawnego rzutowania. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji Typ dynamiczny](../types/using-type-dynamic.md).

     W języku C# 4 osadzanie informacji o typie zamiast używania pias jest zachowaniem domyślnym. Ze względu na to ustawienie domyślne kilka poprzednich przykładów są uproszczone, ponieważ jawne rzutowanie nie jest wymagane. Na przykład deklaracja `worksheet` `DisplayInExcel` w jest `Excel._Worksheet workSheet = excelApp.ActiveSheet` zapisywana jako , a nie `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Wywołania `AutoFit` w tej samej metodzie również wymagałoby `ExcelApp.Columns[1]` jawnego `Object`rzutowania bez domyślnego, ponieważ zwraca , i `AutoFit` jest metodą excel. Poniższy kod pokazuje rzutowanie.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Aby zmienić domyślne i używać piAs zamiast osadzania informacji o typie, rozwiń węzeł **Odwołania** w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Microsoft.Office.Interop.Excel** lub **Microsoft.Office.Interop.Word**.

3. Jeśli nie widzisz okna **Właściwości,** naciśnij klawisz **F4**.

4. Znajdź **embed Interop Types** na liście właściwości i zmień jego wartość na **False**. Podobnie można skompilować przy użyciu opcji [kompilatora -reference](../../language-reference/compiler-options/reference-compiler-option.md) zamiast [-link](../../language-reference/compiler-options/link-compiler-option.md) w wierszu polecenia.

## <a name="to-add-additional-formatting-to-the-table"></a>Aby dodać dodatkowe formatowanie do tabeli

1. Zastąp `AutoFit` dwa `DisplayInExcel` wywołania w następującej instrukcji.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> ma siedem parametrów wartości, z których wszystkie są opcjonalne. Nazwane i opcjonalne argumenty umożliwiają podanie argumentów dla żadnego, niektórych lub wszystkich z nich. W poprzedniej instrukcji argument jest dostarczany tylko dla jednego `Format`z parametrów. Ponieważ `Format` jest to pierwszy parametr na liście parametrów, nie trzeba podawać nazwy parametru. Jednak instrukcja może być łatwiejsze do zrozumienia, jeśli nazwa parametru jest dodany, jak pokazano w poniższym kodzie.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Naciśnij klawisze CTRL+F5, aby zobaczyć wynik. Inne formaty są wymienione <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> w wyliczeniu.

3. Porównaj instrukcję w kroku 1 z następującym kodem, który pokazuje argumenty, które są wymagane w języku C# 3.0 i wcześniejszych wersjach.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Przykład

Poniższy kod przedstawia pełny przykład.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [Dynamiczne](../../language-reference/builtin-types/reference-types.md)
- [Używanie typu dynamicznego](../types/using-type-dynamic.md)
- [Argumenty nazwane i opcjonalne](../classes-and-structs/named-and-optional-arguments.md)
- [Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
