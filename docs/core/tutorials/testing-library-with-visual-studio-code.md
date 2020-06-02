---
title: Testowanie biblioteki klas .NET Standard przy użyciu platformy .NET Core w programie Visual Studio Code
description: Utwórz projekt testu jednostkowego dla biblioteki klas .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292190"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a>Samouczek: testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio Code

W tym samouczku pokazano, jak zautomatyzować testy jednostkowe przez dodanie projektu testowego do rozwiązania.

## <a name="prerequisites"></a>Wymagania wstępne

- Ten samouczek współdziała z rozwiązaniem tworzonym w temacie [Tworzenie biblioteki .NET standard w Visual Studio Code](library-with-visual-studio-code.md).

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. Otwórz program Visual Studio Code.

1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w temacie [tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md).

1. Utwórz projekt testu jednostkowego o nazwie "StringLibraryTest".

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   Szablon projektu tworzy plik UnitTest1.cs o następującym kodzie:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.
   - Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut do `UnitTest1` klasy.
   - Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do zdefiniowania `TestMethod1` .

   Każda metoda oznaczona przy użyciu elementu [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) w klasie testowej oznaczona przy użyciu elementu [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) jest wykonywana automatycznie, gdy test jednostkowy jest uruchamiany.

   > [!NOTE]
   > MSTest jest jednym z trzech platform testowych, spośród których można dokonać wyboru. Inne to xUnit i nUnit.

1. Dodaj projekt testowy do rozwiązania.

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. Utwórz odwołanie do projektu biblioteki klas, uruchamiając następujące polecenie:

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>Dodawanie i uruchamianie metod testów jednostkowych

Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutem w klasie, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutem. Metoda testowa kończy się po znalezieniu pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.

Najczęstsze testy wywołują elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasy. Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu. `Assert`W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod:

| Metody Assert     | Funkcja |
| ------------------ | -------- |
| `Assert.AreEqual`  | Sprawdza, czy dwie wartości lub obiekty są równe. Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe. |
| `Assert.AreSame`   | Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu. Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów. |
| `Assert.IsFalse`   | Sprawdza, czy warunek to `false` . Potwierdzenie kończy się niepowodzeniem, jeśli warunek ma wartość `true` . |
| `Assert.IsNotNull` | Sprawdza, czy obiekt nie jest `null` . Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null` . |

Można również użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metody w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony. Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.

W testowaniu `StringLibrary.StartsWithUpper` metody, należy podać kilka ciągów zaczynających się od wielkiej litery. Oczekiwano, że metoda zwraca `true` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodę. Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery. Oczekiwano, że metoda zwraca `false` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodę.

Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg ( `String.Empty` )](xref:System.String.Empty) i a i `null` ciąg. Pusty ciąg jest taki, który nie zawiera znaków i <xref:System.String.Length> ma wartość 0. `null`Ciąg to taki, który nie został zainicjowany. Można wywołać `StartsWithUpper` bezpośrednio jako metodę statyczną i przekazać pojedynczy <xref:System.String> argument. Lub można wywołać `StartsWithUpper` jako metodę rozszerzającą dla `string` zmiennej przypisanej do `null` .

Zdefiniujesz trzy metody, z których każda wywołuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę wielokrotnie dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się po znalezieniu pierwszego błędu, wywoła Przeciążenie metody, które umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.

Aby utworzyć metody testowe:

1. Otwórz *StringLibraryTest/UnitTest1. cs* i Zastąp cały kod następującym kodem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Test wielkich liter w `TestStartsWithUpper` metodzie zawiera alfabet grecki (u + 0391) oraz wielką literę pauzy (u + 041C). Test małymi literami w `TestDoesNotStartWithUpper` metodzie obejmuje małą literę alfa (u + 03B1) i małą literę cyrylicy GHE (u + 0433).

1. Zapisz zmiany.

1. Uruchom testy:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Dane wyjściowe terminalu pokazują, że wszystkie testy zostały zakończone.

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a>Obsługa niepowodzeń testów

Jeśli wykonujesz programowanie sterowane testami (TDD), najpierw napiszesz testy i nie powiodą się po raz pierwszy. Następnie dodasz kod do aplikacji, która pomyślnie testuje. W takim przypadku został utworzony test po zapisaniu kodu aplikacji, który jest weryfikowany, więc niepowodzenie testu nie powiodło się. Aby sprawdzić, czy test zakończy się niepowodzeniem, gdy spodziewasz się niepowodzeniem, Dodaj nieprawidłową wartość do danych wejściowych testu.

1. Zmodyfikuj `words` tablicę w `TestDoesNotStartWithUpper` metodzie, aby uwzględnić ciąg "Error".

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Uruchom testy:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   Dane wyjściowe terminalu pokazują, że jeden test zakończy się niepowodzeniem i zawiera komunikat o błędzie dla testu zakończonego niepowodzeniem.

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. Cofnij modyfikację w kroku 1 i usuń ciąg "Error". Uruchom ponownie test i testy zakończone powodzeniem.

## <a name="test-the-release-version-of-the-library"></a>Testowanie wersji wydania biblioteki

Teraz, gdy testy zostały zakończone, gdy uruchamiasz wersję debugową biblioteki, Uruchom testy w dodatkowym czasie względem kompilacji wydania biblioteki. Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.

1. Uruchom testy z konfiguracją kompilacji wydania:

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   Testy zostały zakończone pomyślnie.

## <a name="additional-resources"></a>Zasoby dodatkowe

- [Testy jednostkowe w .NET Core i .NET Standard](../testing/index.md)

## <a name="next-steps"></a>Następne kroki

W tym samouczku przetestowano bibliotekę klas. Bibliotekę można udostępniać innym osobom, publikując ją w pakiecie [NuGet](https://nuget.org) jako pakiet. Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:

> [!div class="nextstepaction"]
> [Tworzenie i publikowanie pakietu przy użyciu interfejsu wiersza polecenia dotnet](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

W przypadku opublikowania biblioteki jako pakietu NuGet inne osoby mogą ją zainstalować i używać. Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:

> [!div class="nextstepaction"]
> [Instalowanie i używanie pakietu przy użyciu interfejsu wiersza polecenia dotnet](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

Biblioteka nie musi być dystrybuowana jako pakiet. Można go powiązać z aplikacją konsolową, która go używa. Aby dowiedzieć się, jak opublikować aplikację konsolową, zobacz wcześniejszy samouczek w tej serii:

> [!div class="nextstepaction"]
> [Publikowanie aplikacji konsolowej .NET Core za pomocą Visual Studio Code](publishing-with-visual-studio-code.md)
