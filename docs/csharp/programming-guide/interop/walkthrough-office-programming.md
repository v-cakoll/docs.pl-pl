---
title: 'Wskazówki: Programowanie Office (C# i Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7108ef10333b2ec7aded1b8f768c2953283ac625
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Wskazówki: Programowanie Office (C# i Visual Basic)
Visual Studio oferuje funkcje w języku C# i Visual Basic, zwiększających programowania w języku Microsoft Office. Przydatne funkcje C# obejmują nazwane i opcjonalne argumenty i zwracać wartości typu `dynamic`. W programowaniu modelu COM, można pominąć `ref` — słowo kluczowe i uzyskanie dostępu do właściwości indeksowane. W języku Visual Basic cechy automatycznie implementowane właściwości instrukcje, wyrażenia lambda i inicjatorów kolekcji.

Zarówno języków umożliwiają osadzanie informacji o typie, dzięki czemu wdrożenie zestawy współpracujące ze składnikami modelu COM. bez wdrażania podstawowe zestawy międzyoperacyjne (PIAs) na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
W tym przewodniku przedstawiono te funkcje w kontekście programowania pakietu Office, ale wiele z tych funkcji również są przydatne, ogólnie programowania. W tym przewodnikiem umożliwia aplikacji dodatku Excel utworzyć skoroszyt programu Excel. Następnie należy utworzyć dokument programu Word, zawierającą łącze do skoroszytu. Na koniec zobaczysz sposobu włączania i wyłączania zależności PIA.  
  
## <a name="prerequisites"></a>Wymagania wstępne  

Musi mieć program Microsoft Office Excel i Microsoft Office Word zainstalowanej na komputerze, w tym przewodniku.  
  
 Jeśli używasz systemu operacyjnego, która jest starsza niż [!INCLUDE[windowsver](~/includes/windowsver-md.md)], upewnij się, że [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] jest zainstalowany.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Aby skonfigurować aplikację dodatek programu Excel  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **zainstalowane szablony** okienku rozwiń **Visual Basic** lub **Visual C#**, rozwiń węzeł **Office**, a następnie kliknij przycisk roku wersji Produkt pakietu Office.  
  
4.  W **szablony** okienku, kliknij przycisk **Excel \<wersji > Add-in**.  
  
5.  Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4**, lub nowszym zostanie wyświetlony w **platformy docelowej** pole.  
  
6.  Wpisz nazwę projektu w **nazwa** pole, jeśli chcesz.  
  
7.  Kliknij przycisk **OK**.  
  
8.  Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
### <a name="to-add-references"></a>Aby dodać odwołania  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
2.  Na **zestawy** wybierz opcję **Microsoft.Office.Interop.Excel**, wersja `<version>.0.0.0` (dla klucza produktu numery wersji pakietu Office, zobacz [Versions Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)) w **nazwa składnika** listy, a następnie przytrzymaj klawisz CTRL, klucza i wybierz pozycję **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Jeśli nie ma zestawy, konieczne może być upewnij się, zostaną one zainstalowane i wyświetlane (zobacz [porady: Zainstaluj Office podstawowe zestawy międzyoperacyjne](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).  
  
3.  Kliknij przycisk **OK**.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Aby dodać niezbędne instrukcje importów lub przy użyciu dyrektyw  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisAddIn.vb** lub **ThisAddIn.cs** pliku, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujące `Imports` instrukcje (Visual Basic) lub `using` dyrektywy (C#) na początku pliku kodu, jeśli nie są one już istnieje.  
  
     [!code-csharp[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]

     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]
  
### <a name="to-create-a-list-of-bank-accounts"></a>Aby utworzyć listę kont bank  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **klasy**. Nazwa klasy Account.vb, korzystając z języka Visual Basic lub Account.cs Jeśli używasz języka C#. Kliknij przycisk **Dodaj**.  
  
2.  Zastąp definicję `Account` klasy następującym kodem. Użyj definicje klas *właściwości zaimplementowane automatycznie*. Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-csharp[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]

     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  Aby utworzyć `bankAccounts` listy, która zawiera dwa konta, Dodaj następujący kod do `ThisAddIn_Startup` metody w *ThisAddIn.vb* lub *ThisAddIn.cs*. Użyj deklaracji listy *inicjatory kolekcji*. Aby uzyskać więcej informacji, zobacz [inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-csharp[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]

     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Aby wyeksportować dane do programu Excel  
  
1.  W tym samym pliku Dodaj następującą metodę do `ThisAddIn` klasy. Metoda konfiguruje skoroszytu programu Excel i eksportuje dane do niego.  
  
     [!code-csharp[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]

     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     Dwie nowe C# funkcje są używane w ramach tej metody. Obie te funkcje już istnieje w języku Visual Basic.  
  
    -   Metoda [Dodaj](https://msdn.microsoft.com/library/microsoft.office.interop.excel.workbooks.add.aspx) ma *opcjonalny parametr* służącą do konkretnego szablonu. Parametry opcjonalne nowego [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], można pominąć argumentu dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru. Ponieważ żaden argument są wysyłane w poprzednim przykładzie `Add` korzysta z domyślnego szablonu i tworzy nowy skoroszyt. Odpowiednik instrukcji we wcześniejszych wersjach języka C# wymaga argumentu symbolu zastępczego: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Aby uzyskać więcej informacji, zobacz [nazwane i opcjonalne argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   `Range` i `Offset` właściwości [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) obiekt użyj *właściwości indeksowanych* funkcji. Ta funkcja pozwala korzystać z tych właściwości z typów COM za pomocą następujące typowe składni C#. Właściwości indeksowane pozwalają również na używanie `Value` właściwość `Range` obiektu, eliminując konieczność użycia `Value2` właściwości. `Value` Właściwość jest indeksowana, ale indeks jest opcjonalne. Argumenty opcjonalne właściwości indeksowanych współpracują w poniższym przykładzie.  
  
         [!code-csharp[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         We wcześniejszych wersjach języka następującej składni specjalne jest wymagana.  
  
         [!code-csharp[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Nie można utworzyć właściwości indeksowanych własny. Gdy funkcja obsługuje tylko zużycie istniejącej właściwości indeksowane.  
  
         Aby uzyskać więcej informacji, zobacz [porady: użycie właściwości indeksowanych w programowaniu międzyoperacyjne COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Dodaj następujący kod na końcu `DisplayInExcel` może dostosować szerokości kolumn w celu dopasowania do zawartości.  
  
     [!code-csharp[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]

     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     Te dodatki pokazują innej funkcji w języku C#: traktowanie `Object` wartości zwracane z hostów COM, takich jak Office tak, jakby mają typu [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md). Dzieje się to automatycznie podczas **Osadź typy międzyoperacyjne** ma ustawioną wartość domyślną `True`, lub ekwiwalentnie, gdy zestaw odwołuje się do niego [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) — opcja kompilatora. Typ `dynamic` umożliwia późne wiązanie już dostępna w języku Visual Basic i uniknięcie rzutowania jawnego, wymagane w Visual C# 2008 i starszych wersji języka.  
  
     Na przykład `excelApp.Columns[1]` zwraca `Object`, i `AutoFit` jest Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) metody. Bez `dynamic`, należy rzutować obiektu zwróconego przez `excelApp.Columns[1]` jako wystąpienie `Range` przed wywołaniem metody `AutoFit`.  
  
     [!code-csharp[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Aby uzyskać więcej informacji na temat osadzania typów międzyoperacyjnych Zobacz procedury "Aby odnaleźć odwołania PIA" i "Aby przywrócić zależności PIA" w dalszej części tego tematu. Aby uzyskać więcej informacji na temat `dynamic`, zobacz [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md) lub [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>Aby wywołać DisplayInExcel  
  
1.  Dodaj następujący kod na końcu `ThisAddIn_StartUp` metody. Wywołanie `DisplayInExcel` zawiera dwa argumenty. Pierwszy argument jest nazwą listy kont do przetworzenia. Drugi argument jest wyrażenie wielowierszowych wyrażeń lambda, które określa, jak dane są na przetworzenie. `ID` i `balance` wartości dla każdego konta są wyświetlane w sąsiednich komórek i wiersz jest wyświetlana na czerwono, jeśli saldo jest mniejsza od zera. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-csharp[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]

     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Aby uruchomić program, naciśnij klawisz F5. Pojawia się arkuszu programu Excel, który zawiera dane z konta.  
  
### <a name="to-add-a-word-document"></a>Aby dodać dokument programu Word  
  
1.  Dodaj następujący kod na końcu `ThisAddIn_StartUp` metodę w celu utworzenia dokument programu Word, który zawiera łącze do skoroszytu programu Excel.  
  
     [!code-csharp[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]

     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Ten kod przedstawia niektóre z nowych funkcji w języku C#: możliwość Pomiń `ref` — słowo kluczowe w programowaniu modelu COM, argumenty nazwane i argumenty opcjonalne. Te funkcje są już istnieją w języku Visual Basic. [PasteSpecial](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx) metoda ma siedmiu parametrów, które są zdefiniowane jako parametry opcjonalne informacje dodatkowe. Argumenty nazwane i opcjonalne pozwalają określić parametry, których chcesz uzyskać dostęp według nazwy i przesyłają argumenty tylko tych parametrów. W tym przykładzie argumenty są wysyłane do wskazują, że można utworzyć łącza do skoroszytu w Schowku (parametr `Link`), a łącze ma być wyświetlany w dokumencie programu Word w postaci ikony (parametr `DisplayAsIcon`). Visual C# można również pominąć `ref` — słowo kluczowe dla tych argumentów.
  
### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację. Program Excel i wyświetlenie tabelę, która zawiera informacje z dwóch kont w `bankAccounts`. Dokument programu Word pojawia się zawierającą łącze do tabeli programu Excel.  
  
### <a name="to-clean-up-the-completed-project"></a>Aby wyczyścić projektu zakończone  
  
1.  W programie Visual Studio, kliknij przycisk **czystą rozwiązania** na **kompilacji** menu. W przeciwnym razie dodatek uruchomi zawsze otwierania programu Excel na tym komputerze.  
  
### <a name="to-find-the-pia-reference"></a>Aby znaleźć odwołania PIA  
  
1.  Uruchom ponownie aplikację, ale nie klikaj pozycji **czystą rozwiązania**.  
  
2.  Wybierz **Start**. Zlokalizuj **programu Microsoft Visual Studio \<wersji >** i Otwórz okno wiersza polecenia dewelopera.  
  
3.  Typ `ildasm` w oknie Wiersz polecenia programu Visual Studio, a następnie naciśnij klawisz ENTER. Zostanie wyświetlone okno IL DASM.  
  
4.  Na **pliku** w menu okna IL DASM, wybierz opcję **pliku** > **Otwórz**. Kliknij dwukrotnie **programu Visual Studio \<wersji >**, a następnie kliknij dwukrotnie **projekty**. Otwórz folder dla projektu i Znajdź folder bin/Debug *nazwę projektu*dll. Kliknij dwukrotnie *nazwę projektu*dll. Nowe okno wyświetla atrybuty projektu, oprócz odwołania do innych modułów i zestawów. Należy pamiętać, że przestrzenie nazw `Microsoft.Office.Interop.Excel` i `Microsoft.Office.Interop.Word` znajdują się w zestawie. Domyślnie w programie Visual Studio kompilator importuje typy, które są potrzebne z którym związane są odwołania PIA do używanego zestawu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie zawartości zestawu](../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
5.  Kliknij dwukrotnie **MANIFESTU** ikony. Zostanie wyświetlone okno, który zawiera listę zestawów, zawierające elementy odwołuje się projekt. `Microsoft.Office.Interop.Excel` i `Microsoft.Office.Interop.Word` nie znajdują się na liście. Ponieważ typów, które wymaga projektu zostały zaimportowane do używanego zestawu, odwołania do PIA nie są wymagane. Ułatwia to wdrożenie. PIAs nie muszą znajdować się na komputerze użytkownika, a ponieważ aplikacja nie wymaga wdrożenia określonej wersji PIA, aplikacje mogą służyć do pracy z wielu wersji pakietu Office, pod warunkiem, że niezbędne interfejsów API istnieje we wszystkich wersjach .  
  
     Ponieważ wdrożenia PIAs nie jest już konieczne, można utworzyć aplikację w zaawansowanych scenariuszach, które współpracuje z wielu wersji pakietu Office, w tym wcześniejsze wersje. Jednak to działa tylko wtedy, gdy kodu nie używa żadnych interfejsów API, które nie są dostępne w wersji korzystasz z pakietu Office. Nie jest zawsze jasne, czy określony interfejs API była dostępna w starszej wersji, a dla Przyczyna Praca z wcześniejszych wersji pakietu Office nie jest zalecane.  
  
    > [!NOTE]
    > Pakiet Office nie opublikował PIAs przed pakietu Office 2003. Dlatego jedynym sposobem generowania zestawu międzyoperacyjnego dla pakietu Office 2002 i jego wcześniejsze wersje jest importując odwołania COM.  
  
6.  Zamknij okna manifestu i zestawu.  
  
### <a name="to-restore-the-pia-dependency"></a>Aby przywrócić zależności PIA  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku. Rozwiń węzeł **odwołania** i wybierz polecenie **Microsoft.Office.Interop.Excel**. Naciśnij klawisz F4, aby wyświetlić **właściwości** okna.  
  
2.  W **właściwości**okno, zmień **Osadź typy międzyoperacyjne** właściwość z **True** do **False**.  
  
3.  Powtórz kroki 1 i 2 w ramach tej procedury dla `Microsoft.Office.Interop.Word`.  
  
4.  W języku C# w komentarz dwóch wywołań `Autofit` na końcu `DisplayInExcel` metody.  
  
5.  Naciśnij klawisz F5, aby sprawdzić, czy projekt nadal działa poprawnie.  
  
6.  Powtórz kroki 1 – 3 poprzedniej procedury, aby otworzyć okno zestawu. Zwróć uwagę, że `Microsoft.Office.Interop.Word` i `Microsoft.Office.Interop.Excel` nie są już na liście zestawów osadzonych.  
  
7.  Kliknij dwukrotnie **MANIFESTU** ikony, jak i przewiń listę odwołania do zestawów. Zarówno `Microsoft.Office.Interop.Word` i `Microsoft.Office.Interop.Excel` znajdują się na liście. Ponieważ aplikacja odwołuje się do programu Excel i Word PIAs i **Osadź typy międzyoperacyjne** właściwość jest ustawiona na **False**, oba zestawy musi istnieć na komputerze użytkownika końcowego.  
  
8.  W programie Visual Studio, kliknij przycisk **czystą rozwiązania** na **kompilacji** menu, aby wyczyścić projektu zakończone.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości zaimplementowane automatycznie (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Właściwości zaimplementowane automatycznie (C#)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 [Inicjatory kolekcji](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)  
 [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Wczesne i późne powiązania](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Wyrażenia lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Lambda Expressions (C#)](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Instrukcje: użycie właściwości indeksowanych w programowaniu usługi międzyoperacyjnej modelu COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [Przewodnik: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Przewodnik: Tworzenie pierwszego dodatku VSTO dla programu Excel](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Współdziałanie](../../../csharp/programming-guide/interop/index.md)
