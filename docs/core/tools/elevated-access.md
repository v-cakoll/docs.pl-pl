---
title: Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi poleceń dotnet wymagających podwyższonego poziomu dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156767"
---
# <a name="elevated-access-for-dotnet-commands"></a>Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet

Wskazówki dotyczące tworzenia oprogramowania — Przewodnik po tworzeniu oprogramowania wymagającego najmniejszego poziomu uprawnień. Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora z powodu reguł systemu operacyjnego. Poniższe wskazówki opisują obsługiwane scenariusze pisania oprogramowania przy użyciu programu .NET Core.

Następujące polecenia można uruchomić z podwyższonym poziomem uprawnień:

- `dotnet tool` polecenia, takie jak [Instalacja narzędzia dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nie zalecamy uruchamiania innych poleceń z podwyższonym poziomem uprawnień. W szczególności nie zaleca się podniesienia uprawnień za pomocą poleceń korzystających z programu MSBuild, takich jak [dotnet Restore](dotnet-restore.md), [kompilacja dotnet](dotnet-build.md)i [uruchomienie dotnet](dotnet-run.md). Podstawowym problemem jest problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi między głównym i ograniczonym kontem po wydaniu polecenia dotnet. Może się okazać, że użytkownik z ograniczeniami nie ma dostępu do pliku skompilowanego przez użytkownika root. Istnieją sposoby rozwiązania tej sytuacji, ale nie są one potrzebne do pierwszego miejsca.

Polecenia można uruchamiać jako główne, o ile nie przechodzą z powrotem między głównym i ograniczonym kontem. Na przykład kontenery platformy Docker są domyślnie uruchamiane jako główne, więc mają tę cechę.

## <a name="global-tool-installation"></a>Instalacja narzędzia globalnego

Poniższe instrukcje przedstawiają zalecaną metodę instalowania, uruchamiania i odinstalowywania narzędzi .NET Core, które wymagają podniesionych uprawnień do wykonania.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Zainstaluj narzędzie

Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj poniższe czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania tego katalogu:

- Kliknij prawym przyciskiem myszy folder `%ProgramFiles%\dotnet-tools` i wybierz polecenie **Właściwości**. Zostanie otwarte okno dialogowe **wspólne właściwości** .
- Wybierz kartę **zabezpieczenia** . W obszarze **nazwy grup lub użytkowników**Sprawdź, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania katalogu.
- Jeśli grupa "Użytkownicy" może zapisywać lub modyfikować katalog, użyj innej nazwy katalogu podczas instalowania narzędzi, a nie *narzędzi dotnet*.

Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień. Podczas instalacji zostanie utworzony folder *narzędzi dotnet* .

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Uruchamianie narzędzia globalnego

**Opcja 1** Użyj pełnej ścieżki z podniesionym poziomem uprawnień:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Opcja 2** Dodaj nowo utworzony folder do `%Path%`. Tę operację należy wykonać tylko raz.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

I uruchom z:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstaluj narzędzie globalne

W wierszu polecenia z podwyższonym poziomem uprawnień wpisz następujące polecenie:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Narzędzia lokalne

Narzędzia lokalne są objęte zakresem drzewa dla każdego użytkownika. W przypadku korzystania z podwyższonego poziomu uprawnień narzędzia lokalne udostępniają środowisko użytkownika z ograniczeniami do środowiska z podwyższonym poziomem uprawnień. W systemie Linux i macOS w wyniku tego są ustawiane pliki z dostępem tylko do użytkownika root. Jeśli użytkownik przełączy się z powrotem do konta z ograniczeniami, użytkownik nie będzie mógł uzyskać dostępu do plików ani zapisywać do nich. Instalowanie narzędzi wymagających podniesienia uprawnień jako lokalnych narzędzi nie jest zalecane. Zamiast tego należy użyć opcji `--tool-path` i wcześniejszych wytycznych dla narzędzi globalnych.

## <a name="elevation-during-development"></a>Podniesienie uprawnień podczas opracowywania

Podczas programowania może być potrzebny podwyższony poziom dostępu do testowania aplikacji. Ten scenariusz jest typowy dla aplikacji IoT, na przykład. Zalecamy, aby skompilować aplikację bez podniesienia uprawnień, a następnie uruchomić ją z podniesionymi uprawnieniami. Istnieje kilka wzorców:

- Przy użyciu wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Za pomocą polecenia [dotnet Run](dotnet-run.md) z flagą `—no-build`, aby uniknąć generowania nowych plików binarnych:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Zobacz też

- [Globalne narzędzia platformy .NET Core — Omówienie](global-tools.md)
