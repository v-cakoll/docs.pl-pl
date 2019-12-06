---
title: Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core
description: W tym samouczku wyjaśniono sposób organizowania i testowania projektów programu .NET Core z poziomu wiersza polecenia.
author: cartermp
ms.date: 09/10/2018
ms.custom: seodec18
ms.openlocfilehash: 38017a788a8e43601f49a98230cb4d96e0390061
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884218"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizowanie i testowanie projektów przy użyciu wiersza polecenia platformy .NET Core

Ten samouczek rozpoczyna [się od rozpoczęcia pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia, dzięki](cli-create-console-app.md)czemu nie utworzysz prostej aplikacji konsolowej do tworzenia zaawansowanych i dobrze zorganizowanych aplikacji. Po podaniu, jak używać folderów do organizowania kodu, w tym samouczku pokazano, jak zwiększyć aplikację konsolową za pomocą platformy testowania [xUnit](https://xunit.github.io/) .

## <a name="using-folders-to-organize-code"></a>Organizowanie kodu przy użyciu folderów

Jeśli chcesz wprowadzić nowe typy do aplikacji konsoli, możesz to zrobić przez dodanie plików zawierających typy do aplikacji. Na przykład jeśli dodasz pliki zawierające `AccountInformation` i typy `MonthlyReportRecords` do projektu, struktura pliku projektu jest płaska i łatwa do przechodzenia:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Jednak jest to dobre rozwiązanie tylko wtedy, gdy rozmiar projektu jest stosunkowo mały. Czy można przystąpić do tego, co się stanie, jeśli dodasz 20 typów do projektu? Projekt w nieskończoność nie może być w łatwy sposób przechodzenia i konserwowania w wielu plikach, w których znajduje się katalog główny projektu.

Aby zorganizować projekt, Utwórz nowy folder i nadaj mu nazwę *modele* , aby przechowywać pliki typu. Umieść pliki typu w folderze *modele* :

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, które logicznie grupują pliki do folderów, są łatwe do przechodzenia i konserwowania. W następnej sekcji utworzysz bardziej skomplikowany przykład z użyciem folderów i testów jednostkowych.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organizowanie i testowanie przy użyciu przykładu NewTypes zwierząt domowych

### <a name="building-the-sample"></a>Kompilowanie przykładu

Poniższe kroki można wykonać przy użyciu [przykładowej NewTypes zwierząt domowych](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub utworzyć własne pliki i foldery. Typy są logicznie zorganizowane ze strukturą folderów, która umożliwia dodanie więcej typów później, a testy są również logicznie umieszczane w folderach, co pozwala na dodanie dalszych testów później.

Przykład zawiera dwa typy, `Dog` i `Cat`i ma implementację wspólnego interfejsu, `IPet`. W przypadku projektu `NewTypes` celem jest zorganizowanie typów związanych z PET w folderze *zwierząt domowych* . Jeśli później zostanie dodany inny zestaw typów, *WildAnimals* na przykład, są umieszczane w folderze *NewTypes* obok folderu *zwierzęta* . Folder *WildAnimals* może zawierać typy dla zwierząt, które nie są zwierzętami, takimi jak `Squirrel` i `Rabbit`. W ten sposób, gdy są dodawane typy, projekt pozostaje dobrze zorganizowany.

Utwórz następującą strukturę folderów z wyróżnioną zawartością pliku:

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

```dotnetcli
dotnet run
```

Uzyskaj następujące dane wyjściowe:

```console
Woof!
Meow!
```

Ćwiczenie opcjonalne: można dodać nowy typ PET, taki jak `Bird`, rozszerzając ten projekt. Nadaj metodu `TalkToOwner` ptakowi `Tweet!` do właściciela. Ponownie uruchom aplikację. Dane wyjściowe będą zawierać `Tweet!`

### <a name="testing-the-sample"></a>Testowanie przykładu

Projekt `NewTypes` jest na miejscu i został zorganizowany przez utrzymywanie typów związanych ze zwierzętami ze zwierząt domowych w folderze. Następnie utwórz projekt testowy i zacznij pisać testy za pomocą platformy testów [xUnit](https://xunit.github.io/) . Testy jednostkowe umożliwiają automatyczne sprawdzanie zachowania typów PET w celu potwierdzenia, że działają prawidłowo.

Przejdź z powrotem do folderu *src* i Utwórz folder *testowy* z folderem *NewTypesTests* w nim. W wierszu polecenia w folderze *NewTypesTests* należy wykonać `dotnet new xunit`. Spowoduje to utworzenie dwóch plików: *NewTypesTests. csproj* i *UnitTest1.cs*.

Projekt testowy nie może obecnie testować typów w `NewTypes` i wymaga odwołania projektu do projektu `NewTypes`. Aby dodać odwołanie do projektu, użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Lub można także ręcznie dodać odwołanie do projektu, dodając węzeł `<ItemGroup>` do pliku *NewTypesTests. csproj* :

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

Plik *NewTypesTests. csproj* zawiera następujące elementy:

* Odwołanie do pakietu do `Microsoft.NET.Test.Sdk`, infrastruktura testowa platformy .NET
* Odwołanie do pakietu do `xunit`, struktura testowania xUnit
* Odwołanie do pakietu do `xunit.runner.visualstudio`, moduł uruchamiający testy
* Odwołanie do projektu do `NewTypes`, kod do przetestowania

Zmień nazwę *UnitTest1.cs* na *PetTests.cs* i Zastąp kod w pliku następującym:

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

Opcjonalne ćwiczenie: w przypadku dodania typu `Bird` wcześniej, który generuje `Tweet!` do właściciela, Dodaj metodę testową do pliku *PetTests.cs* , `BirdTalkToOwnerReturnsTweet`, aby sprawdzić, czy metoda `TalkToOwner` działa prawidłowo dla typu `Bird`.

> [!NOTE]
> Chociaż oczekuje się, że wartości `expected` i `actual` są równe, wstępne potwierdzenie ze sprawdzaniem `Assert.NotEqual` określa, że te wartości *nie są równe*. Zawsze należy utworzyć test, aby nie można było sprawdzić logiki testu. Po upewnieniu się, że test zakończy się niepowodzeniem, Dostosuj potwierdzenie, aby zezwolić na przekazanie testu.

Poniżej przedstawiono kompletną strukturę projektu:

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

Uruchom w katalogu *test/NewTypesTests* . Przywróć projekt testowy za pomocą polecenia [`dotnet restore`](../tools/dotnet-restore.md) . Uruchom testy za pomocą polecenia [`dotnet test`](../tools/dotnet-test.md) . To polecenie uruchamia program Test Runner określony w pliku projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Zgodnie z oczekiwaniami testowanie nie powiedzie się, a w konsoli programu zostaną wyświetlone następujące dane wyjściowe:

```output
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

Zmień potwierdzenia testów z `Assert.NotEqual` na `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Uruchom testy za pomocą polecenia `dotnet test` i uzyskaj następujące dane wyjściowe:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Testowanie przebiega. Metody typów PET zwracają poprawne wartości podczas rozmowy z właścicielem.

Wiesz już, jak można organizować i testować projekty przy użyciu xUnit. Przejdź do tych technik, stosując je we własnych projektach. *Radosne kodowanie!*
