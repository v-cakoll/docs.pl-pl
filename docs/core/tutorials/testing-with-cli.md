---
title: Organizowanie i testowanie projektów za pomocą cli .NET Core
description: W tym samouczku wyjaśniono, jak organizować i testować projekty programu .NET Core z wiersza polecenia.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239914"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a>Organizowanie i testowanie projektów za pomocą cli .NET Core

Ten samouczek następuje [Wprowadzenie do .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia,](cli-create-console-app.md)co prowadzi do tworzenia prostej aplikacji konsoli do tworzenia zaawansowanych i dobrze zorganizowanych aplikacji. Po pokazaniu, jak używać folderów do organizowania kodu, w tym samouczku pokazano, jak rozszerzyć aplikację konsoli za pomocą struktury testowania [xUnit.](https://xunit.github.io/)

## <a name="using-folders-to-organize-code"></a>Organizowanie kodu za pomocą folderów

Jeśli chcesz wprowadzić nowe typy do aplikacji na konsolę, możesz to zrobić, dodając do niej pliki zawierające te typy. Na przykład w przypadku `AccountInformation` `MonthlyReportRecords` dodania plików zawierających i typów do projektu struktura plików projektu jest płaska i łatwa w nawigacji:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Jednak to działa dobrze tylko wtedy, gdy rozmiar projektu jest stosunkowo mały. Czy możesz sobie wyobrazić, co się stanie, jeśli dodasz 20 typów do projektu? Projekt na pewno nie będzie łatwy w nawigacji i konserwacji z tym wieloma plikami zaśmiecającymi katalog główny projektu.

Aby zorganizować projekt, utwórz nowy folder i nadać mu nazwę *Modele* do przechowywania plików typów. Umieść pliki typów w folderze *Modele:*

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, które logicznie grupują pliki w foldery, są łatwe w nawigacji i konserwacji. W następnej sekcji utworzysz bardziej złożoną próbkę z folderami i testami jednostkowymi.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Organizowanie i testowanie przy użyciu newtypes zwierzęta próbki

### <a name="building-the-sample"></a>Tworzenie próbki

Aby wykonać następujące kroki, można wykonać wzdłuż za pomocą [NewTypes Zwierzęta próbki](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) lub utworzyć własne pliki i foldery. Typy są logicznie zorganizowane w strukturę folderów, która pozwala na dodanie więcej typów później i testy są również logicznie umieszczone w folderach, co pozwala na dodanie więcej testów później.

Przykład zawiera dwa `Dog` typy `Cat`i , i ma `IPet`je zaimplementować wspólny interfejs, . W `NewTypes` projekcie twoim celem jest zorganizowanie typów związanych ze zwierzętami domowymi w folderze *Zwierzęta domowe.* Jeśli inny zestaw typów zostanie dodany później, *WildAnimals* na przykład, są one umieszczane w *NewTypes* folderu obok *folderu Zwierzęta.* Folder *WildAnimals* może zawierać typy dla zwierząt, które `Squirrel` `Rabbit` nie są zwierzętami domowymi, takie jak i typy. W ten sposób, jak typy są dodawane, projekt pozostaje dobrze zorganizowany.

Utwórz następującą strukturę folderów ze wskazaną zawartością pliku:

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

*IPet.cs:*

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs:*

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs:*

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs:*

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Wykonaj następujące polecenie:

```dotnetcli
dotnet run
```

Uzyskaj następujące dane wyjściowe:

```console
Woof!
Meow!
```

Opcjonalne ćwiczenie: Możesz dodać nowy typ `Bird`zwierzęcia, na przykład , rozszerzając ten projekt. Spraw, aby `TalkToOwner` metoda ptaka dała `Tweet!` właścicielowi. Ponownie uruchom aplikację. Dane wyjściowe obędą się między`Tweet!`

### <a name="testing-the-sample"></a>Testowanie próbki

Projekt `NewTypes` jest na miejscu i zorganizowałeś go, utrzymując typy związane ze zwierzętami domowymi w folderze. Następnie utwórz projekt testowy i rozpocznij pisanie testów za pomocą struktury testów [xUnit.](https://xunit.github.io/) Testowanie jednostkowe pozwala automatycznie sprawdzić zachowanie typów zwierząt domowych, aby potwierdzić, że działają prawidłowo.

Wróć do folderu *src* i utwórz folder *testowy* z folderem *NewTypesTests* w nim. W wierszu polecenia z folderu `dotnet new xunit` *NewTypesTests* wykonaj polecenie . Spowoduje to wygenerowanie dwóch plików: *NewTypesTests.csproj* i *UnitTest1.cs*.

Projekt testowy nie może `NewTypes` obecnie przetestować typów `NewTypes` i wymaga odwołania do projektu. Aby dodać odwołanie do [`dotnet add reference`](../tools/dotnet-add-reference.md) projektu, użyj polecenia:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Lub masz również możliwość ręcznego dodawania odwołania `<ItemGroup>` do projektu, dodając węzeł do pliku *NewTypesTests.csproj:*

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

Plik *NewTypesTests.csproj* zawiera następujące elementy:

* Odwołanie do `Microsoft.NET.Test.Sdk`pakietu , infrastruktury testowania .NET
* Odwołanie do `xunit`pakietu , xUnit testing framework
* Odniesienie do `xunit.runner.visualstudio`opakowania do , biegacza testowego
* Odwołanie do `NewTypes`projektu , kod do testowania

Zmień nazwę *UnitTest1.cs,* aby *PetTests.cs* i zastąpić kod w pliku następującymi nazwami:

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

Opcjonalne ćwiczenie: Jeśli `Bird` wcześniej dodano typ, `Tweet!` który daje właścicielowi, dodaj metodę `BirdTalkToOwnerReturnsTweet`testową do `TalkToOwner` *pliku PetTests.cs,* aby `Bird` sprawdzić, czy metoda działa poprawnie dla tego typu.

> [!NOTE]
> Mimo że można `expected` `actual` oczekiwać, że i wartości `Assert.NotEqual` są równe, wstępne twierdzenie z sprawdzaniem określa, że te wartości nie są *równe*. Zawsze początkowo utworzyć test do niepowodzeniem w celu sprawdzenia logiki testu. Po potwierdzeniu, że test nie powiedzie się, dostosuj potwierdzenie, aby umożliwić test do przejścia.

Poniżej przedstawiono pełną strukturę projektu:

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

Rozpocznij w katalogu *test/NewTypesTests.* Przywróć projekt testowy za [`dotnet restore`](../tools/dotnet-restore.md) pomocą polecenia. Uruchom testy za [`dotnet test`](../tools/dotnet-test.md) pomocą polecenia. To polecenie uruchamia testrunner określony w pliku projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Zgodnie z oczekiwaniami testowanie kończy się niepowodzeniem, a konsola wyświetla następujące dane wyjściowe:

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

Zmień potwierdzeń testów `Assert.NotEqual` z: `Assert.Equal`

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Ponownie uruchom testy za `dotnet test` pomocą polecenia i uzyskaj następujące dane wyjściowe:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Testowanie zdań. Metody typów zwierząt domowych zwracają poprawne wartości podczas rozmowy z właścicielem.

Nauczyłeś się technik organizowania i testowania projektów przy użyciu xUnit. Śmiało z tych technik stosowania ich w swoich własnych projektów. *Szczęśliwego kodowania!*
