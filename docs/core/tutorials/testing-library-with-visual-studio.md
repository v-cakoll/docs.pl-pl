---
title: Testowanie biblioteki klas z platformą .NET Core w Visual Studio 2017 r.
description: Dowiedz się, jak przetestować biblioteki klas napisane w języku C# za pomocą programu Visual Studio 2017 r.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1733f3fc66d79dafb9bc6f983773f043be6c1006
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Testowanie biblioteki klas z platformą .NET Core w Visual Studio 2017 r.

W [tworzenia biblioteki klas C# i .NET Core w Visual Studio 2017](library-with-visual-studio.md) lub [tworzenia biblioteki klas z języka Visual Basic i .NET Core w Visual Studio 2017](vb-library-with-visual-studio.md), utworzyć biblioteki prostą klasę, która dodaje metody rozszerzenia do <xref:System.String> klasy. Teraz utworzysz testu jednostkowego, aby upewnić się, że działa zgodnie z oczekiwaniami. Projekt testowy jednostki zostanie dodana do rozwiązania utworzonego w poprzedniej części tematu.

## <a name="creating-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć jednostkowy projekt testowy, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **ClassLibraryProjects** a następnie wybierz węzeł rozwiązania **Dodaj** > **nowy projekt**.

1. W **Dodawanie nowego projektu** okno dialogowe, wybierz opcję **Visual C#** węzła. Następnie wybierz **.NET Core** węzła następuje **projekt testowy MSTest (.NET Core)** szablonu projektu. W **nazwa** tekst Wprowadź "StringLibraryTest" jako nazwę projektu. Wybierz **OK** utworzyć jednostkowy projekt testowy.

   ![Dodaj okno dialogowe Nowy projekt](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > Oprócz projektu testowego MSTest umożliwia także Visual Studio można utworzyć projektu testowego xUnit dla platformy .NET Core.

1. Visual Studio tworzy projekt i otwiera *UnitTest1.cs* pliku w oknie kodu.

   ![Visual Studio w oknie kod przedstawiający domyślną jednostkę testowania klasa UnitTest1 projektu i TestMethod1 — metoda](./media/testing-library-with-visual-studio/unittestwindow.png)

   Kod źródłowy utworzonej przez szablon testów jednostkowych wykonuje następujące czynności:

   * Importuje [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) przestrzeni nazw, który zawiera typy używane do testowania jednostek.

   * Ma to zastosowanie [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atrybutu `UnitTest1` klasy. Oznaczone do każdej metody w klasie testu \[TestMethod\] atrybutu jest wykonywany automatycznie po uruchomieniu testu jednostkowego.

   * Ma to zastosowanie [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) atrybut do definiowania `TestMethod1` metodą testu do automatycznego wykonania podczas uruchamiania testu jednostkowego.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zależności** węzła **StringLibraryTest** projekt i wybierz **Dodaj odwołanie** z menu kontekstowe.

   ![Menu kontekstowe StringLibraryTest zależności](./media/testing-library-with-visual-studio/addreference.png)

1. W **Menedżera odwołań** okna dialogowego, rozwiń węzeł **projekty** węzła i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodawanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znaleźć **StringLibrary** metody. Wybierz **OK** przycisku. Spowoduje to dodanie odwołania do projektu biblioteki klas `StringLibrary`.

   ![Menedżera odwołań](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **ClassLibraryProjects** a następnie wybierz węzeł rozwiązania **Dodaj** > **nowy projekt**.

1. W **Dodawanie nowego projektu** okno dialogowe, wybierz opcję **Visual Basic** węzła. Następnie wybierz **.NET Core** węzła następuje **projekt testowy MSTest (.NET Core)** szablonu projektu. W **nazwa** tekst Wprowadź "StringLibraryTest" jako nazwę projektu. Wybierz **OK** utworzyć jednostkowy projekt testowy.

   ![Dodaj okno dialogowe Nowy projekt](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > Oprócz projektu testowego MSTest umożliwia także Visual Studio można utworzyć projektu testowego xUnit dla platformy .NET Core.

1. Visual Studio tworzy projekt i otwiera *UnitTest1.vb* pliku w oknie kodu.

   ![Visual Studio w oknie kod przedstawiający domyślną jednostkę testowania klasa UnitTest1 projektu i TestMethod1 — metoda](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   Kod źródłowy utworzonej przez szablon testów jednostkowych wykonuje następujące czynności:

   * Importuje [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) przestrzeni nazw, który zawiera typy używane do testowania jednostek.

   * Ma to zastosowanie [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atrybutu `UnitTest1` klasy. Oznaczone do każdej metody w klasie testu \[TestMethod\] atrybutu jest wykonywany automatycznie po uruchomieniu testu jednostkowego.

   * Ma to zastosowanie [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) atrybut do definiowania `TestMethod1` metodą testu do automatycznego wykonania podczas uruchamiania testu jednostkowego.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zależności** węzła **StringLibraryTest** projekt i wybierz **Dodaj odwołanie** z menu kontekstowe.

   ![Menu kontekstowe StringLibraryTest zależności](./media/testing-library-with-visual-studio/addreference.png)

1. W **Menedżera odwołań** okna dialogowego, rozwiń węzeł **projekty** węzła i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodawanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znaleźć **StringLibrary** metody. Wybierz **OK** przycisku. Spowoduje to dodanie odwołania do projektu biblioteki klas `StringLibrary`.

   ![Menedżera odwołań](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Dodawanie i systemem jednostki metod testowych

Po uruchomieniu programu Visual Studio test jednostkowy wykonywania każdej metody oznaczonej jako [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) atrybut w klasie testu jednostki, klasy, do którego [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) atrybut jest stosowany. Metoda testowa kończy się po napotkaniu pierwszego błędu lub gdy pomyślnie wszystkie testy zawarte w metodzie.

Najbardziej typowe testów wywołania członkami [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) klasy. Assert wiele metod zawierać co najmniej dwóch parametrów, z których jeden jest wynikiem oczekiwany testowy i drugi z nich jest wynikiem testu rzeczywistego. W poniższej tabeli przedstawiono niektóre z jego najczęściej wywoływane metody.

Metody Assert | Funkcja
--- | ---
`Assert.AreEqual` | Sprawdza, czy dwie wartości lub obiekty są takie same. Assert kończy się niepowodzeniem, jeśli nie są takie same wartości lub obiektów.
`Assert.AreSame` | Sprawdza, czy dwie zmienne do obiektu, zapoznaj się z tym samym obiektem. Assert kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.
`Assert.IsFalse` | Sprawdza, czy warunek jest `false`. Assert kończy się niepowodzeniem, jeśli wynikiem warunku jest `true`.
`Assert.IsNotNull` | Sprawdza, czy obiekt nie jest `null`. Assert kończy się niepowodzeniem, jeśli obiekt jest `null`.

Można także zastosować [ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) atrybut do metody testowej. Wskazuje typ metody testowej powinien zgłosić wyjątek. Test zakończy się niepowodzeniem, jeśli określony wyjątek nie jest generowany.

Podczas testowania `StringLibrary.StartsWithUpper` metody chcesz podać liczbę ciągi rozpoczynające się od znaku wielkie litery. Spodziewasz się metody, aby powrócić `true` dlatego w tych przypadkach można wywołać [Assert.IsTrue (wartość logiczna, ciąg)](https://msdn.microsoft.com/library/ms243754.aspx) metody. Podobnie należy podać liczbę ciągi rozpoczynające się z inną niż wielką literę. Spodziewasz się metody, aby powrócić `false` dlatego w tych przypadkach można wywołać [Assert.IsFalse (wartość logiczna, ciąg)](https://msdn.microsoft.com/library/ms243805.aspx) metody.

Ponieważ metodę biblioteki obsługi ciągów, należy upewnić się, że pomyślnie obsługi [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg bez znaków i którego <xref:System.String.Length> ma wartość 0, a `null` ciągu który nie został zainicjowany. Jeśli `StartsWithUpper` zostanie wywołany jako metody rozszerzenia dla <xref:System.String> wystąpienia, go nie mogą być przekazywane `null` ciągu. Można jednak również wywołują go bezpośrednio jako metoda statyczna i przekazać jeden <xref:System.String> argumentu.

Będziesz definiować trzy metody każdego które wywołuje jego [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) metody wielokrotnie dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się, jak najszybciej po napotkaniu pierwszy błąd, wywołujesz przeciążenie metody, która pozwala przekazać ciąg, który wskazuje ciąg używany w wywołaniu metody.

Aby utworzyć metody testowe:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. W *UnitTest1.cs* okno kodu, Zastąp kod następującym kodem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Należy pamiętać, że test z wielkie litery, znaki w `TestStartsWithUpper` metoda zawiera alfa grecki litera (U + 0391) i cyrylicy litera EM (U + 041 C) oraz testu małych liter w `TestDoesNotStartWithUpper` grecki mała litera obejmuje — metoda Alpha (U + 03B1) i cyrylicy małą literę Ghe (U + 0433).

1. Na pasku menu wybierz **pliku** > **Zapisz UnitTest1.cs jako**. W **Zapisz plik jako** okno dialogowe, wybierz strzałkę obok **zapisać** i wybrać **Zapisz z kodowaniem**.

   ![Zapisz plik jako okna dialogowego](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. W *UnitTest1.vb* okno kodu, Zastąp kod następującym kodem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Należy pamiętać, że test z wielkie litery, znaki w `TestStartsWithUpper` metoda zawiera alfa grecki litera (U + 0391) i cyrylicy litera EM (U + 041 C) oraz testu małych liter w `TestDoesNotStartWithUpper` grecki mała litera obejmuje — metoda Alpha (U + 03B1) i cyrylicy małą literę Ghe (U + 0433).

1. Na pasku menu wybierz **pliku** > **Zapisz UnitTest1.vb jako**. W **Zapisz plik jako** okno dialogowe, wybierz strzałkę obok **zapisać** i wybrać **Zapisz z kodowaniem**.

   ![Zapisz plik jako okna dialogowego](./media/testing-library-with-visual-studio/savefileas.png)
---

1. W **Potwierdź zapisywanie jako** okno dialogowe, wybierz opcję **tak** przycisk, aby zapisać plik.

1. W **zaawansowane opcje zapisywania** okno dialogowe, wybierz opcję **Unicode (UTF-8 z podpisem) - strona kodowa 65001** z **kodowanie** listy rozwijanej i wybierz **OK** .

   ![Okno dialogowe Zaawansowane opcje zapisywania](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   Jeśli nie można zapisać jako plik kodowany w formacie UTF8 kodu źródłowego, Visual Studio może ją zapisać jako plik ASCII. W takim przypadku środowisko uruchomieniowe nie dokładnie dekodowania znaków UTF8 poza zakresem ASCII, a wyniki testu będzie dokładne.

1. Na pasku menu wybierz **testu** > **Uruchom** > **wszystkie testy**. **Eksploratora testów** okno otwiera i przedstawia pomyślnie wykonano testy. Trzy testy są wymienione w **przekazany testy** sekcji i **Podsumowanie** sekcji raportów wyników uruchomienia testu.

   ![Okno Eksploratora testów](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>Obsługa niepowodzenia testu

Testu wystąpiły nie błędy, ale jej nieznacznie zmieniać, aby jednej z metod test zakończy się niepowodzeniem:

1. Modyfikowanie `words` tablicy w `TestDoesNotStartWithUpper` metodę w celu uwzględnienia ciąg "Error". Nie trzeba zapisać pliku, ponieważ po utworzeniu rozwiązania do uruchomienia testów programu Visual Studio automatycznie zapisuje otwartych plików.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. Uruchom test, wybierając **Test** > **Uruchom** > **wszystkie testy** na pasku menu. **Eksploratora testów** okna wskazuje, że dwóch testów zakończyła się pomyślnie i jedną nie powiodło się.

   ![Okno Eksploratora testów](./media/testing-library-with-visual-studio/failedtest.png)

1. W **testy nie powiodło się** niepowodzenia testu, wybierz `TestDoesNotStartWith`. **Eksploratora testów** okno wyświetla komunikat produkowane przez assert: "Assert.IsFalse nie powiodło się. Oczekiwano "Błąd": false; rzeczywiste: True ". Z powodu awarii wszystkie ciągi w tablicy po "Error" nie zostały przetestowane.

   ![Okno Eksploratora testów przedstawiający jest False Błąd potwierdzenia](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. Usuń kod, który został dodany (`"Error", `) i uruchomić go ponownie. Testy zostaną spełnione.

## <a name="testing-the-release-version-of-the-library"></a>Testowanie wersji biblioteki

Działała testów z wersją biblioteki debugowania. Testy wszystkich przekazanego i odpowiednio przetestowaniu biblioteki, należy uruchomić testy dodatkowy czas przed kompilacji wydania biblioteki. Wiele czynników, takich jak optymalizacje kompilatora, czasami może wygenerować inaczej między kompilacjami Debug i Release.

Aby przetestować kompilacji wydania:

1. Na pasku narzędzi programu Visual Studio, zmień konfigurację kompilacji z **debugowania** do **wersji**.

   ![Visual Studio paska narzędzi](./media/testing-library-with-visual-studio/toolbar.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **StringLibrary** projekt i wybierz **kompilacji** z menu kontekstowego ponowną kompilację biblioteki.

   ![Menu kontekstowe StringLibrary](./media/testing-library-with-visual-studio/buildlibrary.png)

1. Uruchom testy jednostkowe, wybierając **testu** > **Uruchom** > **wszystkie testy** na pasku menu. Testy zostały zaliczone pomyślnie.

Teraz, po zakończeniu testowania biblioteki, następnym krokiem jest udostępnić obiekty wywołujące. Istnieje możliwość połączenia z co najmniej jednej aplikacji lub opublikować go jako pakietu NuGet. Aby uzyskać więcej informacji, zobacz [korzystających z biblioteki klas .NET Standard](./consuming-library-with-visual-studio.md).
