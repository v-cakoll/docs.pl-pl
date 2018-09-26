---
title: Wdrażanie aplikacji .NET core za pomocą programu Visual Studio
description: Dowiedz się, wdrażanie aplikacji .NET Core za pomocą programu Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7a9410ca99f621ee6d0e8b263354ebc536f71a4a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113835"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>Wdrażanie platformy .NET Core z aplikacji za pomocą programu Visual Studio

Możesz wdrożyć aplikację platformy .NET Core albo jako *wdrożenia zależny od struktury*, który zawiera pliki binarne aplikacji, ale zależy od obecności platformy .NET Core w systemie docelowym lub jako *niezależna wdrożenie*, który zawiera aplikację i pliki binarne .NET Core. Omówienie wdrażania aplikacji .NET Core, zobacz [wdrożenie aplikacji programu .NET Core](index.md).

Poniższe sekcje pokazują, jak używać programu Microsoft Visual Studio do tworzenia następujących rodzajów wdrożenia:

- Wdrożenie zależny od struktury
- Wdrażanie zależny od struktury za pomocą zależności innych firm
- Niezależne wdrożenia
- Niezależne wdrożenia przy użyciu zależności innych firm

Aby uzyskać informacje na temat korzystania z programu Visual Studio do opracowywania aplikacji platformy .NET Core, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).

## <a name="framework-dependent-deployment"></a>Wdrożenie zależny od struktury

Wdrożenie zależny od struktury bez zależności innych firm po prostu polega na tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces.  

1. Utwórz projekt.

   Wybierz **pliku** > **nowe** > **projektu**. W **nowy projekt** okno dialogowe, rozwiń węzeł kategorii danego języka (C# lub Visual Basic) projektu w **zainstalowane** okienku typów projektu, wybierz polecenie **platformy .NET Core**, a następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonów w środkowym okienku. Wprowadź nazwę projektu, takich jak "Dyskietki" w **nazwa** pola tekstowego. Wybierz **OK** przycisku.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* lub *Program.vb* w edytorze i Zastęp automatycznie wygenerowany kod następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Utworzenie kompilacja do debugowania aplikacji.

   Wybierz **kompilacji** > **Kompiluj rozwiązanie**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Wdrażanie aplikacji.

   Po utworzeniu debugowania i przetestować program, należy utworzyć plików do wdrożenia z aplikacją. Aby opublikować z programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.

      1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.

      1. W **Publikuj** zaznacz **Publikuj**. Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.

      1. **Publikuj** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie.

   Pliki wynikowe są umieszczane w katalogu o nazwie `Publish` na Windows i `publish` na komputerach z systemem Unix, które znajduje się w podkatalogu projektu *.\bin\release\netcoreapp2.1* podkatalogu.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdróż kompletny zestaw plików aplikacji w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika. Po zainstalowaniu, użytkownicy mogą następnie wykonać aplikacji przy użyciu `dotnet` polecenia i podając nazwę pliku aplikacji, takich jak `dotnet fdd.dll`.

Oprócz plików binarnych aplikacji Instalatora należy również pakietu Instalatora udostępnionego framework albo Wyszukaj jako warunek wstępny jako część instalacji aplikacji.  Instalacja udostępnionego framework wymaga dostępu administratora/root, ponieważ jest ono komputera.

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>Wdrażanie zależny od struktury za pomocą zależności innych firm

Wdrożenie zależny od struktury z co najmniej jeden zależności innych firm wymaga, aby wszystkie zależności dostępne dla projektu. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go. **Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Należy pamiętać, że wdrożenie zależny od struktury z zależności innych firm tylko jako przenośne jako jego zależności innych firm. Na przykład jeśli biblioteki innych firm obsługuje tylko z systemem macOS, aplikacja nie jest przenośny z systemami Windows. Dzieje się tak, jeśli zależności innych firm, sama jest zależna od kodu natywnego. Dobrym przykładem jest [serwera Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), co wymaga zależności natywnych na [libuv](https://github.com/libuv/libuv). Podczas tworzenia Dyskietki dla aplikacji za pomocą tego rodzaju zależności innych firm opublikowane dane wyjściowe zawiera folder dla każdego [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) obsługującego natywnych zależności (i znajdujące się w pakiecie NuGet).

## <a name="simpleSelf"></a> Niezależne wdrożenia bez zależności innych firm

Wdrożenie niezależna bez zależności innych firm obejmuje tworzenie projektu i modyfikując *csproj* pliku, tworzenia, testowania i publikowania aplikacji. Prosty przykład napisany w języku C# przedstawiono proces. Należy rozpocząć od tworzenia, kodowania i testowania projektu, tak samo jak wdrożenia zależny od struktury:

1. Utwórz projekt.

   Wybierz **pliku** > **nowe** > **projektu**. W **nowy projekt** okno dialogowe, rozwiń węzeł kategorii danego języka (C# lub Visual Basic) projektu w **zainstalowane** okienku typów projektu, wybierz polecenie **platformy .NET Core**, a następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonów w środkowym okienku. Wprowadź nazwę projektu, takich jak "— SCD", w **nazwa** pola tekstowego, a następnie wybierz pozycję **OK** przycisku.

1. Dodawanie kodu źródłowego aplikacji.

   Otwórz *Program.cs* lub plik w edytorze i Zastąp kod wygenerowany automatycznie z następującym kodem. On monituje użytkownika o wprowadzenie tekstu i wyświetla poszczególne wyrazy wprowadzonej przez użytkownika. Używa wyrażenia regularnego `\w+` do oddzielania słów w tekście wejściowym.

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. Określ, czy używać globalizacji niezmiennej trybu.

   Szczególnie w przypadku, gdy aplikacja jest przeznaczona na systemie Linux, można zmniejszyć całkowity rozmiar wdrożenia, wykorzystując [globalizacji niezmiennej tryb](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md). Globalizacji niezmiennej tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture).

   Aby włączyć tryb niezmiennej, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań**i wybierz **Edytuj SCD.csproj** lub **Edytuj SCD.vbproj**. Następnie dodaj następujące wiersze wyróżnione do pliku:

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. Utworzenie kompilacja do debugowania aplikacji.

   Wybierz **kompilacji** > **Kompiluj rozwiązanie**. Można również skompilować i uruchomić kompilację debugowania aplikacji, wybierając **debugowania** > **Rozpocznij debugowanie**. Ten krok debugowania pozwala zidentyfikować problemy z aplikacji, gdy jest uruchomiona na platformie hosta. Nadal trzeba będzie je przetestować na każdej z platform docelowych.

   Po włączeniu trybu niezmiennej globalizacji, należy szczególnie sprawdzić, czy brak dane wrażliwe na ustawienia kulturowe jest odpowiedni dla twojej aplikacji.

Po zakończeniu debugowania, możesz opublikować niezależna wdrożenia:

# <a name="visual-studio-156-and-earliertabvs156"></a>[Visual Studio 15.6 i wcześniejszych](#tab/vs156)

Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.

Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:

1. Zdefiniuj platformy, dla których będzie dotyczyć aplikacji.

   1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Edytuj SCD.csproj**.

   1. Tworzenie `<RuntimeIdentifiers>` tagów w `<PropertyGroup>` części Twojej *csproj* pliku, który definiuje Twojej aplikacji jest przeznaczony dla platform i podaj identyfikator środowiska uruchomieniowego (RID) każdej z platform docelowych. Należy zauważyć, że trzeba będzie również dodać średnika do rozdzielenia identyfikatorów RID. Zobacz [katalog identyfikatora środowiska uruchomieniowego](../rid-catalog.md) Lista identyfikatorów środowisk uruchomieniowych.

   Na przykład w poniższym przykładzie wskazuje, że aplikacja działa w 64-bitowych systemach operacyjnych Windows 10 i 64-bitowym systemie operacyjnym OS X w wersji 10.11.

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   Należy pamiętać, że `<RuntimeIdentifiers>` przejść do dowolnego elementu `<PropertyGroup>` zainstalowanej w swojej *csproj* pliku. Pełny przykład *csproj* plik pojawia się w dalszej części w tej sekcji.

1. Opublikuj aplikację.

   Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla.

   Aby opublikować aplikację z poziomu programu Visual Studio, wykonaj następujące czynności:

      1. Zmień konfigurację przy użyciu rozwiązania **debugowania** do **wersji** na pasku narzędzi do kompilacji w wersji (a nie na debugowanie) wersję aplikacji.

      1. Kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.

      1. W **Publikuj** zaznacz **Publikuj**. Program Visual Studio zapisuje pliki, wchodzące w skład aplikacji w lokalnym systemie plików.

      1. **Publikuj** karta zawiera teraz jeden profil **FolderProfile**. Ustawienia konfiguracji w profilu są wyświetlane w **Podsumowanie** karcie. **Docelowe środowisko uruchomieniowe** identyfikuje, które środowisko uruchomieniowe zostało opublikowane, a **lokalizacji docelowej** identyfikuje, gdzie zostały napisane pliki niezależne wdrożenia.

      1. Visual Studio domyślnie zapisuje pliki wszystkie opublikowane w jednym katalogu. Dla wygody najlepiej jest utworzyć osobne profile dla każdego docelowe środowisko uruchomieniowe i umieść pliki opublikowane w katalogu specyficzny dla platformy. Obejmuje to tworzenie oddzielny profil publikowania dla każdej platformy docelowej. Teraz ponownie skompiluj aplikację dla każdej platformy, wykonując następujące czynności:

         1. Wybierz **Utwórz nowy profil** w **Publikuj** okna dialogowego.

         1. W **wybierz lokalizację docelową publikowania** okno dialogowe, zmiana **wybierz folder** lokalizację *bin\Release\PublishOutput\win10 x64*. Wybierz **OK**.

         1. Wybierz nowy profil (**FolderProfile1**) na liście profilów i upewnij się, że **docelowe środowisko uruchomieniowe** jest `win10-x64`. Jeśli nie, wybierz **ustawienia**. W **ustawienia profilu** okno dialogowe, zmiana **docelowe środowisko uruchomieniowe** do `win10-x64` i wybierz **Zapisz**. W przeciwnym razie wybierz **anulować**.

         1. Wybierz **Publikuj** do publikowania aplikacji dla platformy Windows 10 w 64-bitowych.

         1. Wykonaj poprzednie kroki, aby utworzyć profil dla `osx.10.11-x64` platformy. **Lokalizacji docelowej** jest *bin\Release\PublishOutput\osx.10.11-x64*i **docelowe środowisko uruchomieniowe** jest `osx.10.11-x64`. Nazwa programu Visual Studio, przypisuje do tego profilu jest **FolderProfile2**.

      Należy pamiętać, że każda lokalizacja docelowa zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[Visual Studio 15.7 i nowsze](#tab/vs157)

Po utworzeniu debugowania i przetestować program, należy utworzyć pliki do wdrożenia z aplikacją, dotyczącymi poszczególnych platform, że jest ono przeznaczone dla. Obejmuje to tworzenie osobny profil dla każdej platformy docelowej.

Dla każdej platformy, że Twoje cele aplikacji, wykonaj następujące czynności:

1. Utwórz profil dla danej platformy docelowej.

   Jeśli jest to pierwszy profil został utworzony, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.

   Jeśli już utworzono profil, kliknij prawym przyciskiem myszy projekt, aby otworzyć **Publikuj** okno dialogowe, jeśli nie jest już otwarty. Następnie wybierz pozycję **nowy profil**.

   **Wybierz miejsce docelowe publikowania** zostanie otwarte okno dialogowe.
  
1. Wybierz lokalizację, w którym program Visual Studio publikuje aplikację.

   Jeśli publikujesz tylko na jednej platformie, możesz zaakceptować wartości domyślne w **wybierz folder** pole tekstowe; publikuje wdrożenia zależne struktury aplikacji, aby *\<katalogu projektu > \ bin\Release\netcoreapp2.1\publish\* katalogu.

   Jeśli publikujesz do więcej niż jedną platformę, Dołącz ciąg, który identyfikuje platformę docelową. Na przykład jeśli ciąg "linux" dołączania do ścieżki pliku, programu Visual Studio publikuje wdrożenia zależne struktury aplikacji, aby  *\<katalogu projektu > \bin\Release\netcoreapp2.1\publish\linux*katalogu.

1. Tworzenie profilu, wybierając ikonę listy rozwijanej obok **Publikuj** przycisk i wybierając polecenie **Utwórz profil**. Następnie wybierz pozycję **Utwórz profil** przycisk, aby utworzyć profil.

1. Wskazują, publikują niezależna wdrożenia, a następnie zdefiniuj platformy, przeznaczony dla twojej aplikacji.

   1. W **Publikuj** okno dialogowe, wybierz opcję **Konfiguruj** link umożliwiający otworzenie **ustawienia profilu** okna dialogowego.

   1. Wybierz **niezależna** w **tryb wdrożenia** pola listy.

   1. W **docelowe środowisko uruchomieniowe** pola listy, wybierz jedną z platform, Twoje cele aplikacji.

   1. Wybierz **Zapisz** zaakceptować zmiany i zamknąć okno dialogowe.

1. Nazwa profilu.

   1. Wybierz **akcje** > **Zmienianie nazwy profilu** nazwy profilu.

   2. Przypisywanie profilu nazwa, która określa platformę docelową, a następnie wybierz pozycję **Zapisz*.

Powtórz te kroki, aby zdefiniować żadnych dodatkowych platform, Twoje cele aplikacji.

Skonfigurowano profilów i są teraz gotowe do publikowania aplikacji. W tym celu:

   1. Jeśli **Publikuj** okno nie jest obecnie otwarty, kliknij prawym przyciskiem myszy nad projektem (nie rozwiązanie) **Eksploratora rozwiązań** i wybierz **Publikuj**.

   2. Wybierz profil, który chcesz opublikować, a następnie wybierz **Publikuj**. W tym dla każdego profilu do opublikowania.

   Należy pamiętać, że każda lokalizacja docelowa (w przypadku naszym przykładzie bin\release\netcoreapp2.1\publish\\*nazwa profilu* zawiera kompletny zestaw plików (pliki aplikacji i wszystkich plików z platformy .NET Core) potrzebnych do uruchomienia aplikacji.

Wraz z plikami aplikacji proces publikowania emituje plik bazy danych (PDB) program, który zawiera informacje o debugowaniu dotyczących aplikacji. Plik jest przydatne głównie do debugowania wyjątków. Istnieje możliwość nie spakujesz ją z plikami aplikacji. Jednak należy je zapisać, w przypadku, gdy chcesz debugować kompilację wydania aplikacji.

Wdrażanie plików publikowanych w jakikolwiek sposób, który chcesz. Na przykład, można umieścić je w pliku Zip, użyć prostego `copy` polecenie lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Ponadto program Visual Studio tworzy oddzielny profil publikowania (\*.pubxml) dla każdej z platform docelowych. Na przykład w pliku o naszych profilu systemu linux (linux.pubxml) pojawia się w następujący sposób:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a>Niezależne wdrożenia przy użyciu zależności innych firm

Niezależna wdrożenie z co najmniej jeden zależności innych firm obejmuje dodawanie zależności. Przed utworzeniem aplikacji wymagane są następujące dodatkowe czynności:

1. Użyj **Menedżera pakietów NuGet** Dodaj odwołanie do pakietu NuGet do projektu; i jeśli pakiet nie jest jeszcze dostępna w systemie, zainstaluj go. Aby otworzyć Menedżera pakietów, wybierz **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

1. Upewnij się, że `Newtonsoft.Json` jest zainstalowana w systemie, a jeśli tak nie jest, zainstaluj go. **Zainstalowane** karcie znajduje się lista pakietów NuGet, zainstalowanych w systemie. Jeśli `Newtonsoft.Json` nie ma na liście, wybierz **Przeglądaj** kartę, a następnie wprowadź "Newtonsoft.Json" w polu wyszukiwania. Wybierz `Newtonsoft.Json` i w okienku po prawej stronie, wybierz swój projekt przed wybraniem **zainstalować**.

1. Jeśli `Newtonsoft.Json` jest już zainstalowany w systemie, dodaj go do projektu, wybierając projekt w prawym okienku **Zarządzaj pakietami dla rozwiązania** kartę.

Poniżej przedstawiono pełne *csproj* pliku dla tego projektu:

# <a name="visual-studio-156-and-earliertabvs156"></a>[Visual Studio 15.6 i wcześniejszych](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[Visual Studio 15.7 i nowsze](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

Podczas wdrażania aplikacji, wszelkie zależności innych firm używanych w aplikacji znajdują się również z plikami aplikacji. Bibliotek innych firm nie są wymagane w systemie, na którym działa aplikacja.

Należy pamiętać, że można wdrożyć tylko niezależna wdrożenia przy użyciu biblioteki innej firmy na platformach obsługiwanych przez tej biblioteki. Jest to podobne do mających zależności innych firm za pomocą natywnego zależności w danym wdrożeniu zależny od struktury, gdzie zależności natywnych nie istnieje na platformie docelowej, chyba że zostały wcześniej zainstalowane istnieje.

## <a name="see-also"></a>Zobacz także

* [Wdrożenie aplikacji programu .NET core](index.md)
* [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
