---
title: Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core
description: W tym samouczku wyjaśniono, jak organizowanie i testowanie projektów .NET Core z poziomu wiersza polecenia.
author: cartermp
ms.author: mairaw
ms.date: 09/10/2018
ms.openlocfilehash: 8131e51577bcad9191c0cacb61317fa146bf476d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025496"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core

W tym samouczku następuje [rozpoczęcie pracy z platformą .NET Core w Windows/Linux/macOS przy użyciu wiersza polecenia](using-with-xplat-cli.md), otwieranie poza tworzenia aplikacji konsolowej proste do tworzenia zaawansowanych i dobrze zorganizowanego aplikacji. Po pokazujący, jak używać folderów do organizowania kodu, w tym samouczku dowiesz się, jak rozszerzyć aplikację konsoli przy użyciu [xUnit](https://xunit.github.io/) struktury testowania.

## <a name="using-folders-to-organize-code"></a>Za pomocą folderów do organizowania kodu

Wprowadzenie nowych typów do aplikacji konsoli, możesz to zrobić, dodając pliki zawierające typów aplikacji. Na przykład w przypadku dodania plików zawierających `AccountInformation` i `MonthlyReportRecords` typów do projektu, struktura pliku projektu jest daje płaski i nawigację:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Jednak ta działa tylko w dobrze po stosunkowo mały rozmiar projektu. Możesz sobie wyobrazić co się stanie po dodaniu 20 typów do projektu? Zdecydowanie projektu nie być łatwe do nawigowania i obsługa z tym wiele plików littering katalogu głównego projektu.

Aby zorganizować projekt, Utwórz nowy folder i nadaj mu nazwę *modeli* do przechowywania plików typu. Umieść pliki typu do *modeli* folderu:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, które logicznie grupy plików do folderów, które są łatwe do nawigowania i obsługa. W następnej sekcji utworzysz przykładowe bardziej złożonych z folderów i testy jednostkowe.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organizowanie i testowanie, korzystając z przykładu zwierzęta NewTypes

### <a name="building-the-sample"></a>Budowanie przykładu

Dla następujących kroków możesz albo kontynuować pracę przy użyciu [przykładowe zwierzęta NewTypes](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub tworzyć własne pliki i foldery. Typy są logicznie pogrupowane w strukturę folderów, która zezwala na dodawanie większej liczby typów później, a testy również logicznie są umieszczane w folderach, umożliwiające dodanie więcej testów później.

Przykład zawiera dwa typy `Dog` i `Cat`i ma mu w zaimplementowaniu wspólny interfejs `IPet`. Aby uzyskać `NewTypes` projektu, dowiesz się, jak organizowania typów powiązanych pet do *zwierzęta* folderu. Jeśli inny zestaw typów zostanie dodany później *WildAnimals* na przykład, są umieszczane w *NewTypes* folder wraz z *zwierzęta* folderu. *WildAnimals* folderu może zawierają typy służące do zwierząt, które nie są zwierząt domowych, takich jak `Squirrel` i `Rabbit` typów. W ten sposób podczas dodawania typów projektu pozostaje dobrze zorganizowane. 

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

Wykonaj następujące polecenie:

```console
dotnet run
```

Uzyskaj następujące dane wyjściowe:

```console
Woof!
Meow!
```

Opcjonalne Ćwiczenia: można dodać nowy typ domowych, takich jak `Bird`, rozszerzając tego projektu. Należy z lotu ptaka `TalkToOwner` zapewniają metody `Tweet!` do właściciela. Ponownie uruchom aplikację. Dane wyjściowe będą zawierać `Tweet!`

### <a name="testing-the-sample"></a>Badanie próbki

`NewTypes` Projektu w miejscu, a ułożone ją, przechowując typy związane z zwierzęta w folderze. Następnie utwórz projekt testu i zacząć pisać testy z [xUnit](https://xunit.github.io/) struktury testowej. Testy jednostkowe umożliwia automatyczne sprawdzenie dostępności bevahior pet typów, aby upewnić się, że są one działających prawidłowo.

Tworzenie *test* folder z *NewTypesTests* folder znajdujący się w nim. W wierszu polecenia z *NewTypesTests* folderu wykonaj `dotnet new xunit`. Pozwala to na utworzenie dwóch plików: *NewTypesTests.csproj* i *UnitTest1.cs*.

Projekt testowy nie może obecnie testowanie typów w `NewTypes` i wymaga odwołania projektu do `NewTypes` projektu. Aby dodać odwołanie do projektu, należy użyć [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Istnieje również opcja ręcznego dodawania odwołania projektu, dodając `<ItemGroup>` węzeł *NewTypesTests.csproj* pliku:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* plik zawiera następujące czynności:

* Odwołanie do pakietu `Microsoft.NET.Test.Sdk`, .NET, testowanie infrastruktury
* Odwołanie do pakietu `xunit`, xUnit, struktury testowania
* Odwołanie do pakietu `xunit.runner.visualstudio`, narzędzia test runner
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

Opcjonalne Ćwiczenia: Jeśli dodano `Bird` wcześniej typ, który daje `Tweet!` do właściciela, należy dodać metody testowej, aby *PetTests.cs* pliku `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy `TalkToOwner` metoda działa prawidłowo dla `Bird` typu.

> [!NOTE]
> Mimo że można oczekiwać, że `expected` i `actual` wartości są równe, początkowe potwierdzenie z `Assert.NotEqual` wyboru określa, czy te wartości są *równa*. Zawsze utworzyć test, aby zakończyć się niepowodzeniem, aby sprawdzić logikę testu. Po upewnieniu się, że test zakończy się niepowodzeniem, należy dostosować potwierdzenie, aby zezwolić na test kończył się pomyślnie.

Poniżej przedstawiono strukturę kompletnego projektu:

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

Rozpocznij w *testów/NewTypesTests* katalogu. Przywróć projekt testowy z [ `dotnet restore` ](../tools/dotnet-restore.md) polecenia. Uruchom testy przy użyciu [ `dotnet test` ](../tools/dotnet-test.md) polecenia. To polecenie uruchamia narzędzie test runner, określone w pliku projektu.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Zgodnie z oczekiwaniami, testowania kończy się niepowodzeniem i konsoli wyświetlane następujące wyniki:

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

Zmień potwierdzenia testów z `Assert.NotEqual` do `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Ponownie uruchom testy z `dotnet test` polecenia i uzyskać następujące wyniki:

```
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Testowanie przebiegów. Typów pet zwracają poprawne wartości w przypadku do właściciela.

Wyjaśniono techniki organizowanie i testowanie projektów przy użyciu xUnit. Przejdź do przodu, za pomocą tych metod, stosując je do własnych projektów. *Udanego kodowania!*

