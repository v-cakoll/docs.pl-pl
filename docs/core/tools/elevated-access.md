---
title: Podwyższony dostęp dla poleceń dotnet
description: Poznaj najlepsze rozwiązania dotyczące poleceń dotnet, które wymagają podwyższonego dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156767"
---
# <a name="elevated-access-for-dotnet-commands"></a>Podwyższony dostęp dla poleceń dotnet

Najlepsze rozwiązania dotyczące tworzenia oprogramowania prowadzą deweloperów do pisania oprogramowania, które wymaga najmniejszej ilości uprawnień. Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora ze względu na reguły systemu operacyjnego. W poniższych wskazówkach opisano obsługiwane scenariusze pisania takiego oprogramowania za pomocą programu .NET Core.

Z podwyższonym poziomem uprawnień można uruchomić następujące polecenia:

- `dotnet tool`polecenia, takie jak [instalacja narzędzia dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nie zaleca się uruchamiania innych poleceń z podwyższonym poziomem uprawnień. W szczególności nie zaleca się podniesienia uprawnień z poleceniami, które używają MSBuild, takie jak [przywracanie dotnet,](dotnet-restore.md) [kompilacja dotnet](dotnet-build.md)i [uruchamianie dotnet](dotnet-run.md). Podstawowym problemem są problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi tam iz powrotem między głównym i konta z ograniczeniami po wydaniu poleceń dotnet. Jako użytkownik z ograniczeniami może okazać się, że nie masz dostępu do pliku utworzonego przez użytkownika głównego. Istnieją sposoby, aby rozwiązać tę sytuację, ale są one niepotrzebne, aby dostać się w pierwszej kolejności.

Polecenia można uruchamiać jako root tak długo, jak długo nie przechodzisz tam iz powrotem między głównym a kontem z ograniczeniami. Na przykład kontenery platformy Docker są domyślnie uruchamiane jako katalog główny, więc mają tę charakterystykę.

## <a name="global-tool-installation"></a>Globalna instalacja narzędzi

Poniższe instrukcje pokazują zalecany sposób instalowania, uruchamiania i odinstalowywania narzędzi programu .NET Core, które wymagają uprawnień z podwyższonym poziomem uprawnień do wykonania.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Zainstaluj narzędzie

Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj następujące czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do zapisu lub modyfikowania tego katalogu:

- Kliknij prawym `%ProgramFiles%\dotnet-tools` przyciskiem myszy folder i wybierz polecenie **Właściwości**. Zostanie otwarte okno dialogowe **Właściwości wspólne.**
- Wybierz kartę **Zabezpieczenia.** W **obszarze Nazwy grup lub użytkowników**sprawdź, czy grupa "Użytkownicy" ma uprawnienia do zapisu lub modyfikowania katalogu.
- Jeśli grupa "Użytkownicy" może zapisywać lub modyfikować katalog, podczas instalowania narzędzi należy użyć innej nazwy katalogu niż *narzędzi dotnet*.

Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu z podwyższonym poziomem uprawnień. Podczas instalacji utworzy folder *narzędzi dotnet.*

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Uruchamianie narzędzia globalnego

**Wariant 1** Użyj pełnej ścieżki z podwyższonym poziomem uprawnień:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Wariant 2** Dodaj nowo utworzony folder `%Path%`do pliku . Wystarczy wykonać tę operację tylko raz.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

I uruchomić z:

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

Narzędzia lokalne są objęte zakresem dla drzewa podkatalogu, na użytkownika. Po uruchomieniu z podwyższonym poziomem uprawnień narzędzia lokalne współużytkują ograniczone środowisko użytkownika z podwyższonym poziomem uprawnień. W systemach Linux i macOS powoduje to ustawienie plików z dostępem tylko dla użytkownika głównego. Jeśli użytkownik przełączy się z powrotem na konto z ograniczeniami, użytkownik nie może już uzyskać dostępu do plików ani zapisywać ich. Dlatego nie zaleca się instalowania narzędzi wymagających podniesienia uprawnień jako narzędzi lokalnych. Zamiast tego `--tool-path` użyj opcji i poprzednich wytycznych dla narzędzi globalnych.

## <a name="elevation-during-development"></a>Elewacja podczas rozwoju

Podczas tworzenia aplikacji może być konieczne podwyższony dostęp do testowania aplikacji. Ten scenariusz jest typowy dla aplikacji IoT, na przykład. Zaleca się utworzenie aplikacji bez elewacji, a następnie uruchomienie jej z rzędną. Istnieje kilka wzorców, w następujący sposób:

- Przy użyciu wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Za pomocą polecenia [dotnet run](dotnet-run.md) z flagą, `—no-build` aby uniknąć generowania nowych plików binarnych:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Zobacz też

- [Omówienie podstawowych narzędzi globalnych .NET](global-tools.md)
