---
title: 'Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcje — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 9163bfa98d85a3268e154321d1aa6e55783a50f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347643"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji (C# Programming Guide)
Visual C# zawiera funkcje, które ułatwiają dostęp do obiektów interfejsu API usługi Office. Nowe funkcje obejmują argumentów nazwanych i opcjonalnych, nowy typ o nazwie `dynamic`oraz możliwość przekazywania argumentów do parametrów odwołania w metodach COM tak, jakby były one wartości parametrów.  
  
 W tym temacie użyjesz nowych funkcji do pisania kodu, które tworzy i wyświetla arkusz programu Microsoft Office Excel. Następnie napiszesz kod, aby dodać dokument programu Word pakietu Office, który zawiera ikonę która jest połączona w arkuszu programu Excel.  
  
 Do przeprowadzenia tego instruktażu, musi mieć Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowszy zainstalowany na tym komputerze.  
  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli  
  
1. Uruchom program Visual Studio.  
  
2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**. **Nowy projekt** pojawi się okno dialogowe.  
  
3. W **zainstalowane szablony** okienku rozwiń **Visual C#** , a następnie kliknij przycisk **Windows**.  
  
4. Szukaj w górnej części **nowy projekt** upewnij się, że okno dialogowe **.NET Framework 4** (lub nowsza wersja) został wybrany jako platforma docelowa.  
  
5. W **szablony** okienku kliknij **aplikację Konsolową**.  
  
6. Wpisz nazwę dla projektu w **nazwa** pola.  
  
7. Kliknij przycisk **OK**.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
## <a name="to-add-references"></a>Aby dodać odwołania  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** pojawi się okno dialogowe.  
  
2. Na **zestawy** wybierz opcję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy, a następnie przytrzymaj naciśnięty klawisz CTRL, klucza i wybierz pozycję  **Microsoft.Office.Interop.Excel**.  Jeśli nie ma zestawów, może być konieczne upewnić się, są zainstalowane i wyświetlane (zobacz [jak: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3. Kliknij przycisk **OK**.  
  
## <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne dyrektyw using  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **Wyświetl kod**.  
  
2. Dodaj następujący kod `using` dyrektywy na górze pliku kodu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]  
  
## <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bankowych  
  
1. Wklej poniższą definicję klasy do **Program.cs**w obszarze `Program` klasy.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]  
  
2. Dodaj następujący kod do `Main` metodę w celu utworzenia `bankAccounts` lista, która zawiera dwa konta.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]  
  
## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Do deklarowania metody, które Eksportuje informacje o koncie do programu Excel  
  
1. Dodaj następującą metodę do `Program` klasy arkusza programu Excel.  
  
     Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma parametr opcjonalny służącą do konkretnego szablonu. Parametry opcjonalne nowego w programie C# 4, umożliwiają pominięto argument dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument nie jest wysyłany w poniższym kodzie `Add` korzysta z domyślnego szablonu i utworzy nowy skoroszyt. Równoważne instrukcji we wcześniejszych wersjach języka C# wymaga argumentu symbolu zastępczego: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]  
  
2. Dodaj następujący kod na końcu `DisplayInExcel`. Kod wstawia wartości na pierwszych dwóch kolumn będących jej pierwszego wiersza arkusza.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]  
  
3. Dodaj następujący kod na końcu `DisplayInExcel`. `foreach` Pętli umieszcza informacje z listy kont do kolumn pierwszych dwóch następujących po sobie wierszy arkusza.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]  
  
4. Dodaj następujący kod na końcu `DisplayInExcel` można dostosowywać szerokość kolumn w celu dopasowania do zawartości.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]  
  
     Wcześniejszych wersjach języka C# wymaga jawnego rzutowania dla tych operacji, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` nadaje się program Excel <xref:Microsoft.Office.Interop.Excel.Range> metody. Poniższe wiersze pokazują rzutowania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
     C#4 i nowsze wersje, konwertuje zwracane `Object` do `dynamic` automatycznie, jeśli odwołuje się zestaw [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) — opcja kompilatora lub ekwiwalentnie, jeśli programu Excel **Osadź typy współdziałania** właściwość jest ustawiona na wartość true. Wartość true, to wartością domyślną dla tej właściwości.  
  
## <a name="to-run-the-project"></a>Aby uruchomić projekt  
  
1. Dodaj następujący wiersz na końcu `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]  
  
2. Naciśnij kombinację klawiszy CTRL + F5.  
  
     Arkusz programu Excel pojawi się zawierającej dane z dwóch kont.  
  
## <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word  
  
1. Aby zilustrować dodatkowych sposobów, w którym C# 4 i nowsze wersje, rozszerza programowaniu pakietu Office, otwiera aplikację Word poniższy kod i tworzy ikony, który stanowi łącze do arkusza programu Excel.  
  
     Wklej metodę `CreateIconInWordDoc`, podane w dalszej części tego kroku do `Program` klasy. `CreateIconInWordDoc` używa argumentów nazwanych i opcjonalnych, aby zmniejszyć złożoność wywołania metody do <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> i <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Te wywołania zestawowi dwóch innych nowych funkcji wprowadzonych w C# 4, które upraszczają wywołania metody COM, które mają odwołania do parametrów. Po pierwsze może wysyłać argumentów do parametrów w formie odwołań, tak, jakby były one wartości parametrów. Oznacza to można wysyłać wartości bezpośrednio, bez tworzenia zmienną dla każdego parametru odwołania. Kompilator generuje tymczasowe zmienne do przechowywania wartości argumentów i odrzuca wszystkie zmienne, po powrocie z wywołania. Po drugie, można pominąć `ref` — słowo kluczowe na liście argumentów.  
  
     `Add` Metoda ma cztery parametry odwołań, które są opcjonalne. W C# 4.0 i nowsze wersje, możesz pominąć argumenty poszczególnych lub wszystkich parametrów, jeśli chcesz użyć wartości domyślnych. W C# 3.0 i wcześniejszych wersji, należy podać argument dla każdego parametru, a argument musi być zmienną, ponieważ parametry są parametry odwołania.  
  
     `PasteSpecial` Metoda Wstawia zawartość Schowka. Metoda ma siedem parametrów odwołania, które są opcjonalne. Poniższy kod określa argumenty dwa z nich: `Link`, aby utworzyć łącze do źródła zawartości Schowka i `DisplayAsIcon`, aby wyświetlić łącza w postaci ikony. W C# 4.0 i nowsze wersje, możesz użyć nazwanych argumentów dla tych dwóch i Pomiń pozostałe. Mimo, że są to parametry odwołania, trzeba użyć `ref` — słowo kluczowe, lub aby utworzyć zmienne do wysyłania jako argumenty. Wartości można wysyłać bezpośrednio. W C# 3.0 i wcześniejszych wersji, należy podać zmiennych argumentów dla każdego parametru odwołania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]  
  
     W C# 3.0 i wcześniejszych wersji języka, że wymagane jest bardziej skomplikowanym kodzie.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]  
  
2. Na koniec należy dodać następującą instrukcję `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]  
  
3. Na koniec należy dodać następującą instrukcję `DisplayInExcel`. `Copy` Metoda dodaje arkusz do Schowka.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]  
  
4. Naciśnij kombinację klawiszy CTRL + F5.  
  
     Dokument programu Word wyświetlany jest wyświetlana ikona. Kliknij dwukrotnie ikonę Aby przenieść arkusza na pierwszym planie.  
  
## <a name="to-set-the-embed-interop-types-property"></a>Aby ustawić właściwość Osadź typy międzyoperacyjne  
  
1. Dodatkowe rozszerzenia są możliwe w przypadku, gdy wywołujesz typ modelu COM, który nie wymaga podstawowego zestawu międzyoperacyjnego (PIA) w czasie wykonywania. Eliminujące zależność od wyników zestawów PIA w niezależność i łatwiejsze wdrażanie. Aby uzyskać więcej informacji na temat korzyści programowanie bez zestawów PIA, zobacz [instruktażu: Osadzanie typów z zarządzanych zestawów](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
     Ponadto programowania jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody COM mogą być reprezentowane za pomocą typu `dynamic` zamiast `Object`. Zmienne, które mają typ `dynamic` nie są sprawdzane do czasu wykonywania, który eliminuje konieczność jawnego rzutowania. Aby uzyskać więcej informacji, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     W C# 4, osadzanie typów informacji zamiast przy użyciu zestawów PIA jest zachowanie domyślne. Z powodu tej wartości domyślnej kilka poprzednich przykładach są uproszczone, ponieważ jawne Rzutowanie nie jest wymagane. Na przykład deklaracja `worksheet` w `DisplayInExcel` jest zapisywany jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` zamiast `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Wywołania `AutoFit` w tej samej metody również wymaga jawnego rzutowania bez domyślnego, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` jest metodą programu Excel. Poniższy kod przedstawia rzutowania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
2. Aby zmienić domyślny i używanie zestawów PIA, zamiast osadzanie informacji o typie, rozwiń węzeł **odwołania** w węźle **Eksploratora rozwiązań** , a następnie wybierz **Microsoft.Office.Interop.Excel** lub **Microsoft.Office.Interop.Word**.  
  
3. Jeśli nie widzisz **właściwości** naciśnij klawisze **F4**.  
  
4. Znajdź **Osadź typy współdziałania** na liście właściwości i zmień jej wartość na **False**. Ekwiwalentnie można kompilować przy użyciu [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora zamiast [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) polecenie w wierszu polecenia.  
  
## <a name="to-add-additional-formatting-to-the-table"></a>Aby dodać dodatkowe formatowanie do tabeli  
  
1. Zastąp dwa wywołania `AutoFit` w `DisplayInExcel` przy użyciu następujących instrukcji.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]  
  
     <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda zawiera siedem wartości parametrów, z których wszystkie są opcjonalne. Argumenty nazwane i opcjonalne umożliwiają argumenty dla żadnego, niektórych lub wszystkich z nich. W poprzednich instrukcji, argument jest dostarczany tylko dla jednego z parametrów, `Format`. Ponieważ `Format` jest pierwszym parametrem na liście parametrów, nie należy podać nazwę parametru. Jednak instrukcja może być łatwiejsze do zrozumienia, jeśli nazwa parametru jest uwzględniany, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]  
  
2. Naciśnij klawisze CTRL + F5, aby wyświetlić wynik. Inne formaty są wymienione w <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> wyliczenia.  
  
3. Porównaj z instrukcją w kroku 1, z użyciem następujący kod, który wyświetla argumenty, które są wymagane w C# 3.0 i wcześniejszych wersji.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia kompletny przykład.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
