---
title: "Porady: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C# (Przewodnik po programowaniu w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 751e8240c9385f516315ff3b53221d1e1348ae58
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Porady: uzyskiwanie dostępu do obiektów międzyoperacyjności pakietu Office za pomocą funkcji Visual C# (Przewodnik po programowaniu w języku C#)
Visual C# ma funkcje, które ułatwiają dostęp do interfejsu API usługi Office obiektów. Nowe funkcje obejmują argumenty nazwane i opcjonalne, nowy typ o nazwie `dynamic`i umożliwia przekazywanie argumentów do parametrów odwołania w metodach COM, tak jakby były wartości parametrów.  
  
 W tym temacie użyjesz nowe funkcje do pisania kodu, które tworzy i wyświetla arkusz programu Microsoft Office Excel. Następnie napiszesz kod, aby dodać dokument programu Word pakietu Office, który zawiera ikonę, która jest połączona w arkuszu programu Excel.  
  
 W tym przewodniku, musi mieć Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowszy zainstalowany na tym komputerze.  
  
 Jeśli używasz systemu operacyjnego, która jest starsza niż [!INCLUDE[windowsver](~/includes/windowsver-md.md)], upewnij się, że [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] jest zainstalowany.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku rozwiń **Visual C#**, a następnie kliknij przycisk **Windows**.  
  
4.  Szukaj w górnej części **nowy projekt** okno dialogowe, aby upewnić się, że **.NET Framework 4** (lub nowszym) jest wybrany jako platforma docelowa.  
  
5.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
6.  Wpisz nazwę projektu w **nazwa** pola.  
  
7.  Kliknij przycisk **OK**.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
### <a name="to-add-references"></a>Aby dodać odwołania  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
2.  Na **zestawy** wybierz pozycję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy, a następnie przytrzymaj klawisz CTRL, klucza i wybierz pozycję  **Microsoft.Office.Interop.Excel**.  Jeśli nie ma zestawy, konieczne może być upewnij się, zostaną one zainstalowane i wyświetlane (zobacz [porady: Zainstaluj Office podstawowe zestawy międzyoperacyjne](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3.  Kliknij przycisk **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne przy użyciu dyrektyw  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujące `using` dyrektywy na początku pliku kodu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bank  
  
1.  Wklej następujący definicji klasy do **Program.cs**w obszarze `Program` klasy.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]  
  
2.  Dodaj następujący kod do `Main` metodę w celu utworzenia `bankAccounts` listy, która zawiera dwa konta.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]  
  
### <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Aby zadeklarować metodę, która eksportuje informacje o koncie do programu Excel  
  
1.  Dodaj następującą metodę do `Program` klasa do konfigurowania programu Excel.  
  
     Metoda [Dodaj](https://msdn.microsoft.com/library/microsoft.office.interop.excel.workbooks.add.aspx) ma parametr opcjonalny służącą do konkretnego szablonu. Parametry opcjonalne nowego [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], można pominąć argumentu dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument są wysyłane w poniższym kodzie `Add` korzysta z domyślnego szablonu i tworzy nowy skoroszyt. Odpowiednik instrukcji we wcześniejszych wersjach języka C# wymaga argumentu symbolu zastępczego: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  Dodaj następujący kod na końcu `DisplayInExcel`. Kod wstawia wartości na pierwszych dwóch kolumnach pierwszego wiersza w arkuszu.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]  
  
3.  Dodaj następujący kod na końcu `DisplayInExcel`. `foreach` Pętli umieszcza informacje z listy kont do pierwszych dwóch kolumnach kolejnych wierszach arkusza.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]  
  
4.  Dodaj następujący kod na końcu `DisplayInExcel` może dostosować szerokości kolumn w celu dopasowania do zawartości.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]  
  
     Wcześniejszych wersjach języka C# wymaga jawnego rzutowania dla takich operacji, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` jest Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) metody. Poniższe wiersze pokazują rzutowania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
     [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]i nowszych wersjach, konwertuje zwróconego `Object` do `dynamic` automatycznie, jeśli odwołuje się zestaw [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) — opcja kompilatora lub ekwiwalentnie, jeśli programu Excel **Osadź typy międzyoperacyjne**właściwość jest ustawiona na true. Wartość true, jest to wartość domyślna dla tej właściwości.  
  
### <a name="to-run-the-project"></a>Aby uruchomić projekt  
  
1.  Dodaj następujący wiersz na końcu `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]  
  
2.  Naciśnij klawisze CTRL + F5.  
  
     Pojawia się arkuszu programu Excel, który zawiera dane z dwóch kont.  
  
### <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word  
  
1.  Aby zilustrować dodatkowe sposoby, w którym [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]i nowszych wersjach zwiększa Office programowania, poniższy kod otwiera aplikację Word i tworzy ikonę prowadzący w arkuszu programu Excel.  
  
     Wklej metody `CreateIconInWordDoc`, podane w dalszej części tego kroku do `Program` klasy. `CreateIconInWordDoc`używa argumentów nazwanych i opcjonalnych uproszczeniu wywołań metody [Dodaj](https://msdn.microsoft.com/library/microsoft.office.interop.word.documents.add.aspx) i [PasteSpecial](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx). Te wywołania uwzględnienie dwóch innych nowych funkcji wprowadzonych w [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] który uprościć wywołań do metod modelu COM, które mają parametry odwołania. Najpierw można wysłać argumenty parametrów odwołania, tak jakby były wartości parametrów. Oznacza to, że można wysyłać wartości bezpośrednio, bez tworzenia zmienną dla każdego parametru odwołania. Kompilator generuje tymczasowego zmienne do przechowywania wartości argumentów i odrzuca wszystkie zmienne, po powrocie z wywołania. Po drugie, można pominąć `ref` — słowo kluczowe w liście argumentów.  
  
     `Add` Metoda ma cztery parametry odwołania, które są opcjonalne. W [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], lub nowszych wersji, można pominąć argumenty dla dowolnego lub wszystkich parametrów, jeśli chcesz użyć wartości domyślnych. W [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] i wcześniejsze wersje, należy podać argument dla każdego parametru i argument musi być zmienną, ponieważ parametry są parametry odwołania.  
  
     `PasteSpecial` Metody Wstawia zawartość Schowka. Metoda ma siedmiu parametrów odwołania, które są opcjonalne. Poniższy kod określa argumenty dla dwóch z nich: `Link`, aby utworzyć łącze do źródła zawartości Schowka i `DisplayAsIcon`, aby wyświetlić łącza w postaci ikony. W [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], można użyć nazwane argumenty dla tych dwóch i Pomiń pozostałe. Mimo że te są parametry odwołanie, nie należy użyć `ref` — słowo kluczowe, lub aby utworzyć zmienne do wysłania jako argumenty. Możesz wysłać wartości bezpośrednio. W [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] i starszych wersjach, musisz wysłać zmiennych argumentów dla każdego parametru odwołania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     W [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] i jego wcześniejsze wersje języka następujące bardziej złożonego kodu jest wymagane.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  Dodaj następującą instrukcję na końcu `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]  
  
3.  Dodaj następującą instrukcję na końcu `DisplayInExcel`. `Copy` Metoda dodaje arkusz do Schowka.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]  
  
4.  Naciśnij klawisze CTRL + F5.  
  
     Dokument programu Word wyświetlany jest wyświetlana ikona. Kliknij dwukrotnie ikonę się na pierwszym planie przełączenie w arkuszu.  
  
### <a name="to-set-the-embed-interop-types-property"></a>Aby ustawić właściwości Osadź typy międzyoperacyjne  
  
1.  Dodatkowe rozszerzenia są możliwe w przypadku wywołania typu modelu COM, który nie wymaga podstawowy zestaw międzyoperacyjny (PIA) w czasie wykonywania. Usuwa jego zależność od wyników PIAs w wersji niezależność i łatwiejsze wdrożenia. Aby uzyskać więcej informacji na temat korzyści programowania bez PIAs, zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
     Ponadto programowania jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody modelu COM może być reprezentowany przez przy użyciu typu `dynamic` zamiast `Object`. Zmienne, które mają typ `dynamic` nie są oceniane do czasu wykonywania, która eliminuje potrzebę stosowania rzutowania jawnego. Aby uzyskać więcej informacji, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     W [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], osadzanie informacji o typie zamiast PIAs jest zachowanie domyślne. Z powodu tego domyślnie kilka poprzednich przykładach są uproszczone, ponieważ jawne Rzutowanie nie jest wymagane. Na przykład deklaracja `worksheet` w `DisplayInExcel` są zapisywane jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` zamiast `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Wywołania `AutoFit` w tej samej metody również wymaga jawnego rzutowania bez domyślnych, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` jest metodą programu Excel. Poniższy kod przedstawia rzutowania.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
2.  Aby zmienić ustawienie domyślne i użyć PIAs zamiast osadzanie informacji o typie, rozwiń **odwołania** w węźle **Eksploratora rozwiązań** , a następnie wybierz **Microsoft.Office.Interop.Excel** lub **Microsoft.Office.Interop.Word**.  
  
3.  Jeśli nie widzisz **właściwości** naciśnij klawisze **F4**.  
  
4.  Znajdź **Osadź typy międzyoperacyjne** na liście właściwości i zmień wartość na **False**. Ekwiwalentnie można skompilować przy użyciu [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora zamiast [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) w wierszu polecenia.  
  
### <a name="to-add-additional-formatting-to-the-table"></a>Aby dodać dodatkowe formatowanie do tabeli  
  
1.  Zastąp dwóch wywołań `AutoFit` w `DisplayInExcel` z następującą instrukcję.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]  
  
     [Autoformatowanie](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat.aspx) metoda ma siedmiu wartości parametrów, które są opcjonalne. Argumenty nazwane i opcjonalne umożliwiają stosowanie argumentów none, niektóre lub wszystkie z nich. W poprzednich instrukcji argumentu tylko dla jednego z parametrów, `Format`. Ponieważ `Format` jest pierwszym parametrem na liście parametrów, nie musisz podać nazwę parametru. Jednak instrukcja może być łatwiejsze do zrozumienia, jeśli nazwa parametru jest uwzględnione, jak to pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]  
  
2.  Naciśnij klawisze CTRL + F5, aby zobaczyć wynik. Inne formaty są wymienione w [XlRangeAutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.xlrangeautoformat.aspx) wyliczenia.  
  
3.  Porównaj z instrukcją w kroku 1 z następującym kodem, który zawiera argumenty, które są wymagane w [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] i jego wcześniejsze wersje.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia pełny przykład.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type.Missing?displayProperty=nameWithType>  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
