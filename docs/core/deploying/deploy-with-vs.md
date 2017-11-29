---
title: "Wdrażanie aplikacji .NET core z programem Visual Studio"
description: "Dowiedz się, wdrażanie aplikacji .NET Core z programem Visual Studio"
keywords: "Wdrożenie .NET Core .NET i .NET core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.openlocfilehash: 884ecb110b4168c6dc1e4c664de1dcb8db3734c5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>Wdrażanie .NET Core aplikacji za pomocą programu Visual Studio

Możesz wdrożyć aplikację .NET Core albo jako *wdrożenia zależne od framework*, który zawiera pliki binarne z aplikacji, ale zależy od obecności .NET Core w systemie docelowym lub jako *niezależne wdrożenie*, w tym aplikacji i plików binarnych .NET Core. Omówienie wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](index.md).

W poniższych sekcjach przedstawiono sposób użycia programu Microsoft Visual Studio można utworzyć następujące typy wdrożeń:

- Zależne od Framework wdrożenia
- Wdrożenie Framework zależne zależności innych firm
- Samodzielne wdrożenia
- Samodzielne wdrożenia zależności innych firm

Informacje w celu projektowania aplikacji .NET Core za pomocą programu Visual Studio, zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Zależne od Framework wdrożenia

Po prostu wdrażanie wdrożenia zależne od framework bez zależności innych firm obejmuje tworzenie, testowanie i publikowanie aplikacji. Prosty przykład napisane w języku C# przedstawiono proces.  

1. Tworzenie projektu.

   Select **File** > **New** > **Project**. W **nowy projekt** okno dialogowe, wybierz opcję **.NET Core** w **zainstalowana** okienko typy projektu i wybierz **aplikacji konsoli (.NET Core)** szablon w środkowym okienku. Wprowadź nazwę projektu, na przykład "Dyskietki" w **nazwa** pola tekstowego. Wybierz **OK** przycisku.

1. Należy dodać kodu źródłowego aplikacji.

   Otwórz *Program.cs* plik w edytorze i Zastąp następujący kod automatycznie wygenerowany kod. Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **kompilacji** > **zbudować rozwiązanie**. Można również skompilować i uruchomić kompilacji debugowania aplikacji przez wybranie **debugowania** > **Rozpocznij debugowanie**.

1. Wdrażanie aplikacji.

   Po debugowania i przetestowane programu, tworzenia plików do wdrożenia z aplikacją. Aby opublikować w programie Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratora rozwiązań**i wybierz **publikowania**.

      1. W **publikowania** wybierz opcję **publikowania**. Visual Studio zapisuje pliki, które składają się z lokalnym systemem plików przez aplikację.

      1. **Publikowania** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** sekcji karty.

   Pliki wynikowe są umieszczane w katalogu o nazwie `PublishOutput` w podkatalogu projektu *.\bin\release* podkatalogu.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji. Plik przydaje się głównie w celu debugowania wyjątków. Możesz nie można skopiować pliki aplikacji. Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdróż pełny zestaw plików aplikacji w dowolny sposób, który chcesz. Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika. Po zainstalowaniu użytkowników można następnie uruchamiać aplikacji przy użyciu `dotnet` polecenia i podania nazwy pliku aplikacji, takich jak `dotnet fdd.dll`.

Oprócz plików binarnych aplikacji instalatorem należy również pakietu Instalatora udostępnionego framework albo wyszukać jako warunek wstępny jako część instalacji aplikacji.  Instalacja udostępnionego framework wymaga dostępu administratora/root, ponieważ jest ona komputera.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrożenie Framework zależne zależności innych firm

Wdrażanie wdrożenie zależne od framework z co najmniej jeden zależności innych firm wymaga, aby wszelkie zależności dostępne do projektu. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie i, jeśli nie jest, zainstaluj go. **Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** i wprowadzić "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie wybierz projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowana na komputerze, dodaj go do projektu po wybraniu projektu w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Należy pamiętać, że wdrożenie framework zależne zależności innych firm tylko jako przenośne jako jego zależności innych firm. Na przykład jeśli biblioteka innych firm obsługuje tylko macOS, aplikacja nie jest przenośne z systemami Windows. Dzieje się tak, jeśli zależności innych firm, sama zależy od kodu natywnego. Dobrym przykładem jest [serwera Kestrel](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), co wymaga natywnego zależności na [libuv](https://github.com/libuv/libuv). Podczas tworzenia Dyskietki dla aplikacji z tego rodzaju zależności innych firm publikowanych danych wyjściowych zawiera folder dla każdej [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnego zależności (i znajdujące się w pakiecie NuGet).

## <a name="simpleSelf"></a>Samodzielne wdrożenia bez zależności innych firm

Wdrażanie niezależne wdrożenia bez zależności innych firm obejmuje utworzenie projektu, modyfikując *csproj* plików, tworzenie, testowanie i publikowanie aplikacji. Prosty przykład napisane w języku C# przedstawiono proces. 

1. Tworzenie projektu.

   Select **File** > **New** > **Project**. W **Dodawanie nowego projektu** okno dialogowe, wybierz opcję **.NET Core** w **zainstalowana** okienko typy projektu i wybierz **aplikacji konsoli (.NET Core)** szablon w środkowym okienku. Wprowadź nazwę projektu, na przykład "SCD" w **nazwa** pola tekstowego, a następnie wybierz **OK** przycisku.

1. Należy dodać kodu źródłowego aplikacji.

   Otwórz *Program.cs* plik w edytorze i zastąpić automatycznie wygenerowany kod następującym kodem. Monituje użytkownika o wprowadzenie tekstu, a Wyświetla poszczególnych wyrazów wprowadzony przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w wejściowego tekstu.

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. Zdefiniuj platformy, dla których aplikacja będzie obowiązywać.

   1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj**.

   1. Utwórz `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojego *csproj* pliku, który definiuje celów aplikacji platformy i określ identyfikator środowiska uruchomieniowego (RID) każdej z platform docelowych. Należy pamiętać, że należy również dodać średnika do rozdzielenia identyfikatorów RID. Zobacz [katalogu identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla identyfikatorów środowiska wykonawczego. 

   Na przykład poniższy przykład oznacza, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X 10.11 wersji.

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   Należy pamiętać, że `<RuntimeIdentifiers>` elementu można przejść do dowolnego `<PropertyGroup>` zainstalowanej w Twojej *csproj* pliku. Kompletnego przykładu *csproj* plik pojawi się później w tej sekcji.

1. Utwórz kompilację debugowania aplikacji.

   Wybierz **kompilacji** > **zbudować rozwiązanie**. Można również skompilować i uruchomić kompilacji debugowania aplikacji przez wybranie **debugowania** > **Rozpocznij debugowanie**.

1. Publikowanie aplikacji.

   Po debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją dla poszczególnych platform jej celem.

   Aby opublikować aplikację z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację rozwiązania z **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersji aplikacji.

      1. Kliknij prawym przyciskiem myszy projekt (nie rozwiązanie) w **Eksploratora rozwiązań** i wybierz **publikowania**. 

      1. W **publikowania** wybierz opcję **publikowania**. Visual Studio zapisuje pliki, które składają się z lokalnym systemem plików przez aplikację.

      1. **Publikowania** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** sekcji karty. **Docelowe środowisko uruchomieniowe** identyfikuje, które środowiska wykonawczego został opublikowany, i **lokalizacji docelowej** identyfikuje, gdzie zostały zapisane pliki niezależne wdrożenia.

      1. Visual Studio domyślnie zapisuje pliki wszystkie opublikowane do jednego katalogu. Dla wygody najlepiej jest utworzenie osobnych profilów dla każdej docelowe środowisko uruchomieniowe i umieścić pliki opublikowane w katalogu specyficzne dla platformy. Obejmuje to tworzenie oddzielny profil publikowania dla każdej platformy docelowej. Dlatego teraz odbudować aplikacji dla poszczególnych platform w następujący sposób:

         1. Wybierz **Utwórz nowy profil** w **publikowania** okna dialogowego.

         1. W **wybierz element docelowy publikowania** okna dialogowego, zmień **wybierz folder** lokalizacji *bin\Release\PublishOutput\win10 x64*. Wybierz **OK**.

         1. Wybierz nowy profil (**FolderProfile1**) na liście profilów i upewnij się, że **docelowe środowisko uruchomieniowe** jest `win10-x64`. Jeśli nie, wybierz **ustawienia**. W **ustawienia profilu** okna dialogowego, zmień **docelowe środowisko uruchomieniowe** do `win10-x64` i wybierz **zapisać**. W przeciwnym razie wybierz **anulować**.

         1. Wybierz **publikowania** do publikowania aplikacji dla 64-bitowej platformy systemu Windows 10.

         1. Wykonaj poprzednie kroki, aby ponownie utworzyć profil dla `osx.10.11-x64` platformy. **Lokalizacji docelowej** jest *bin\Release\PublishOutput\osx.10.11-x64*i **docelowe środowisko uruchomieniowe** jest `osx.10.11-x64`. Nazwa programu Visual Studio przypisuje do tego profilu jest **FolderProfile2**.

      Należy pamiętać, że każda lokalizacja docelowa zawiera pełny zestaw plików (pliki aplikacji i wszystkich plików .NET Core) potrzebne do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (.pdb) program, który zawiera informacje o debugowaniu aplikacji. Plik przydaje się głównie w celu debugowania wyjątków. Możesz nie można skopiować pliki aplikacji. Jednak należy go zapisać, w przypadku, gdy chcesz debugować kompilacji wersji aplikacji.

Wdrażanie plików publikowanych w dowolny sposób, który chcesz. Na przykład można umieścić je w pliku Zip, użyć prostej `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełną *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Samodzielne wdrożenia zależności innych firm

Wdrażanie niezależne wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie i, jeśli nie jest, zainstaluj go. **Zainstalowana** karta zawiera listę pakietów NuGet zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** i wprowadzić "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie wybierz projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowana na komputerze, dodaj go do projektu po wybraniu projektu w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Poniżej przedstawiono pełną *csproj* pliku dla tego projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

Podczas wdrażania aplikacji, wszelkie zależności innych firm używane w aplikacji znajdują się również z plikami aplikacji. Biblioteki innych firm nie są wymagane na komputerze, na którym jest uruchomiona aplikacja.

Należy pamiętać, że można wdrożyć tylko autonomiczną wdrożenia z biblioteką innych firm na platformach obsługiwanych przez tej biblioteki. Przypomina mających zależności innych firm z natywnego zależności w danym wdrożeniu zależne od framework gdzie natywnego zależności nie istnieje na platformie docelowej, chyba że zostały one wcześniej zainstalowane.

# <a name="see-also"></a>Zobacz także
[Wdrażanie aplikacji .NET core](index.md)   
[Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)   
