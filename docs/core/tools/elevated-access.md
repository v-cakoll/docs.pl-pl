---
title: Podwyższony dostęp do poleceń dotnet
description: Poznaj najlepsze rozwiązania dotyczące poleceń dotnet, które wymagają podwyższonego dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: f99e0b257772e0a73d4945f1129997d1d3308ed2
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805790"
---
# <a name="elevated-access-for-dotnet-commands"></a>Podwyższony dostęp do poleceń dotnet

Najlepsze rozwiązania w zakresie tworzenia oprogramowania prowadzą programistów do pisania oprogramowania, które wymaga najmniejszej ilości uprawnień. Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora ze względu na reguły systemu operacyjnego. W poniższych wskazówkach opisano obsługiwane scenariusze pisania takiego oprogramowania za pomocą programu .NET Core.

Można uruchomić następujące polecenia z podwyższonym poziomem uprawnień:

- `dotnet tool`polecenia, takie jak [instalowanie narzędzia dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`
- `dotnet-core-uninstall`

Nie zaleca się uruchamiania innych poleceń z podwyższonym poziomem uprawnień. W szczególności nie zaleca się podniesienia poziomu za pomocą poleceń korzystających z msbuild, takich jak [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md)i [dotnet run](dotnet-run.md). Podstawowym problemem są problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi tam iz powrotem między kontem głównym a kontem z ograniczeniami po wydaniu poleceń dotnet. Możesz znaleźć jako użytkownik z ograniczeniami, że nie masz dostępu do pliku utworzonego przez użytkownika root. Istnieją sposoby, aby rozwiązać tę sytuację, ale są one niepotrzebne, aby dostać się w pierwszej kolejności.

Polecenia można uruchamiać jako katalog główny, o ile nie przechodzisz między kontem głównym a kontem z ograniczeniami. Na przykład kontenery platformy Docker są domyślnie uruchamiane jako katalog główny, więc mają tę cechę.

## <a name="global-tool-installation"></a>Globalna instalacja narzędzi

Poniższe instrukcje pokazują zalecany sposób instalowania, uruchamiania i odinstalowywania narzędzi .NET Core, które wymagają uprawnień z podwyższonym poziomem uprawnień do wykonania.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Zainstaluj narzędzie

Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj następujące czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do pisania lub modyfikowania tego katalogu:

- Kliknij prawym `%ProgramFiles%\dotnet-tools` przyciskiem myszy folder i wybierz polecenie **Właściwości**. Zostanie otwarte okno dialogowe **Właściwości wspólne.**
- Wybierz kartę **Zabezpieczenia.** W obszarze **Nazwy grup lub użytkowników**sprawdź, czy grupa "Użytkownicy" ma uprawnienia do pisania lub modyfikowania katalogu.
- Jeśli grupa "Użytkownicy" może napisać lub zmodyfikować katalog, użyj innej nazwy katalogu podczas instalowania narzędzi, a nie *dotnet-tools*.

Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu z podwyższonym poziomem uprawnień. Utworzy folder *dotnet-tools* podczas instalacji.

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Uruchamianie narzędzia globalnego

**Wariant 1** Użyj pełnej ścieżki z podwyższonym poziomem monitu:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Wariant 2** Dodaj nowo utworzony `%Path%`folder do pliku . Tę operację należy wykonać tylko raz.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

I biegać z:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalowywanie narzędzia globalnego

W wierszu z podwyższonym poziomem uprawnień wpisz następujące polecenie:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[Macos](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Narzędzia lokalne

Narzędzia lokalne są objęte zakresem dla drzewa podkatalogu na użytkownika. Po uruchomieniu podwyższonego poziomu narzędzia lokalne współużytkują ograniczone środowisko użytkownika w środowisku podwyższonego poziomu. W systemach Linux i macOS powoduje to, że pliki są ustawiane z dostępem tylko dla użytkowników root. Jeśli użytkownik przełączy się z powrotem do konta z ograniczeniami, użytkownik nie może już uzyskać dostępu do plików ani ich zapisu. Dlatego instalowanie narzędzi, które wymagają podniesienia poziomu jako narzędzi lokalnych, nie jest zalecane. Zamiast tego użyj `--tool-path` opcji i poprzednich wytycznych dotyczących narzędzi globalnych.

## <a name="elevation-during-development"></a>Wysokość podczas rozwoju

Podczas tworzenia może być potrzebny podwyższony dostęp do testowania aplikacji. Ten scenariusz jest typowy dla aplikacji IoT, na przykład. Zaleca się tworzenie aplikacji bez podniesienia, a następnie uruchomić go z podniesieniem. Istnieje kilka wzorów, w następujący sposób:

- Korzystanie z wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Używanie polecenia [dotnet](dotnet-run.md) run `—no-build` z flagą w celu uniknięcia generowania nowych plików binarnych:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Zobacz też

- [Omówienie narzędzi globalnych .NET Core](global-tools.md)
