---
title: Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core
description: W tym samouczku opisano sposób organizowania i testowanie projektów .NET Core w wierszu polecenia.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: a49eb1d398ab80a4ece703b7889083ea967df862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217646"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core

W tym samouczku wykonuje [Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia](using-with-xplat-cli.md), otwieranie poza tworzenie aplikacji konsoli simple do opracowywania zaawansowanych i dobrze zorganizowane aplikacji. Po przedstawiający sposób używania folderów do organizowania kodu, w tym samouczku przedstawiono sposób rozszerzyć aplikacji konsoli z [xUnit](https://xunit.github.io/) testowania framework.

## <a name="using-folders-to-organize-code"></a>Organizowanie kodu za pomocą folderów

Aby dodać nowe typy w aplikacji konsoli, możesz to zrobić przez dodanie plików zawierających typy do aplikacji. Na przykład możesz dodać pliki zawierające `AccountInformation` i `MonthlyReportRecords` typów do projektu, struktura pliku projektu jest prosty i nawigację:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Jednak to działa tylko oraz gdy jest stosunkowo mały rozmiar projektu. Można w pewnym sensie co się stanie po dodaniu 20 typów do projektu? Ostatecznie projektu nie będą łatwe do nawigowania i obsługa z tym wiele plików littering katalog główny projektu.

Aby zorganizować projektu, Utwórz nowy folder i nadaj mu nazwę *modele* do przechowywania plików typu. Umieścić pliki typu *modele* folderu:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, które logicznie grupy plików w folderach łatwych do nawigowania i obsługa. W następnej sekcji utworzysz próbkę bardziej złożonych z folderami i testowania jednostek.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organizowanie i testowania przy użyciu przykładowych zwierząt domowych NewTypes

### <a name="building-the-sample"></a>Tworzenie przykładowej

Dla następujących kroków, można to wykonać przy użyciu [NewTypes zwierząt domowych próbki](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub tworzyć własne pliki i foldery. Typy są logicznie pogrupowane w struktury folderów, która pozwala na dodanie większej liczby typów później, a testy również logicznie są umieszczane w folderach umożliwiający dodanie większej liczby testów później.

Próbka zawiera dwa typy `Dog` i `Cat`i ich implementacji wspólny interfejs ma `IPet`. Dla `NewTypes` projektu, jest organizowania typów związanych z pet do *zwierząt domowych* folderu. Jeśli później dodać inny zestaw typów *WildAnimals* na przykład jest umieszczany w *NewTypes* folderu obok *zwierząt domowych* folderu. *WildAnimals* folder może zawierać typy zwierząt, które nie są zwierząt domowych, takich jak `Squirrel` i `Rabbit` typów. W ten sposób jako typy są dodawane, projekt pozostaje również zorganizowany. 

Utwórz następującą strukturę folderów z zawartością pliku wskazanego:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Uruchom następujące polecenia:

```console
dotnet run
```

Uzyskaj następujące dane wyjściowe:

```console
Woof!
Meow!
```

Ćwiczenie opcjonalne: można dodać nowy typ domowych, takich jak `Bird`, rozszerzając tego projektu. Wprowadź ptaka `TalkToOwner` podać metodę `Tweet!` do właściciela. Ponownie uruchom aplikację. Dane wyjściowe będą zawierać `Tweet!`

### <a name="testing-the-sample"></a>Testowanie próbki

`NewTypes` Projektu jest już na miejscu i ułożone go przechowując powiązane zwierząt domowych typów w folderze. Następnie utwórz projekt testowy i rozpocząć pisanie testów z [xUnit](https://xunit.github.io/) struktury testowej. Testy jednostkowe umożliwia automatyczne sprawdzenie dostępności bevahior pet typów, aby upewnić się, że są one poprawnie działających.

Utwórz *test* folder o *NewTypesTests* folderze. W wierszu polecenia z *NewTypesTests* folderu, wykonać `dotnet new xunit`. To tworzy dwa pliki: *NewTypesTests.csproj* i *UnitTest1.cs*.

Projekt testowy nie może obecnie przetestować typów w `NewTypes` i wymaga odwołania projektu do `NewTypes` projektu. Aby dodać odwołanie do projektu, należy użyć [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Masz również możliwość ręcznie dodać odwołanie do projektu, dodając `<ItemGroup>` węzeł *NewTypesTests.csproj* pliku:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* plik zawiera następujące:

* Odwołanie do pakietu `Microsoft.NET.Test.Sdk`, .NET testowania infrastruktury
* Odwołanie do pakietu `xunit`, xUnit testowania framework
* Odwołanie do pakietu `xunit.runner.visualstudio`, uruchamiający
* Odwołanie do projektu `NewTypes`, kod do testowania

Zmień nazwę *UnitTest1.cs* do *PetTests.cs* i Zastąp kod w pliku następującym kodem:

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

Opcjonalne wykonywania: Jeśli dodano `Bird` wcześniej typu, który daje `Tweet!` do właściciela, Dodaj metodę testu *PetTests.cs* pliku `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy `TalkToOwner` metoda działa poprawnie na `Bird` typu.

> [!NOTE]
> Mimo że oczekuje, że `expected` i `actual` wartości są równe, początkowej potwierdzenia z `Assert.NotEqual` kontroli Określ, czy są one *równa*. Zawsze początkowo tworzenie testów niepowodzenie raz w celu sprawdzenia logiki testów. Jest to ważny krok metodologii test-driven projektu (TDD). Po upewnieniu się, że testy zostaną zakończone niepowodzeniem, możesz dostosować potwierdzenia umożliwia im to do przekazania.

Poniżej przedstawiono struktury kompletnego projektu:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Uruchom w *testu/NewTypesTests* katalogu. Przywracanie projektu testowego z [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia. Uruchom testy z [ `dotnet test` ](../tools/dotnet-test.md) polecenia. To polecenie uruchamia uruchamiający określony w pliku projektu.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Zgodnie z oczekiwaniami, testowania kończy się niepowodzeniem i konsoli wyświetla następujące dane wyjściowe:
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

Zmień potwierdzenia testów `Assert.NotEqual` do `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Ponownie uruchom testy z `dotnet test` poleceń i uzyskać następujące dane wyjściowe:

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

Testowanie przejścia. Metody typów pet zwracać poprawnych wartości komunikuje się z właścicielem.

Znasz już techniki organizowanie i testowanie projektów przy użyciu xUnit. Przejdź do przodu z tych metod, stosując je do własnych projektów. *Kodowanie przyjemność!*

