---
title: Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi poleceń dotnet wymagających podwyższonego poziomu dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: b6de87f375a584da25e160d79f51f1bc48f3c302
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969862"
---
# <a name="elevated-access-for-dotnet-commands"></a>Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet

Wskazówki dotyczące tworzenia oprogramowania — Przewodnik po tworzeniu oprogramowania wymagającego najmniejszego poziomu uprawnień. Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora z powodu reguł systemu operacyjnego. Poniższe wskazówki opisują obsługiwane scenariusze pisania oprogramowania przy użyciu programu .NET Core. 

Następujące polecenia można uruchomić z podwyższonym poziomem uprawnień:

- `dotnet tool`polecenia, takie jak [Instalacja narzędzia dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nie zalecamy uruchamiania innych poleceń z podwyższonym poziomem uprawnień. W szczególności nie zaleca się podniesienia uprawnień za pomocą poleceń korzystających z programu MSBuild, takich jak [dotnet Restore](dotnet-restore.md), [kompilacja dotnet](dotnet-build.md)i [uruchomienie dotnet](dotnet-run.md). Podstawowym problemem jest problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi między głównym i ograniczonym kontem po wydaniu polecenia dotnet. Może się okazać, że użytkownik z ograniczeniami nie ma dostępu do pliku skompilowanego przez użytkownika root. Istnieją sposoby rozwiązania tej sytuacji, ale nie są one potrzebne do pierwszego miejsca.

Polecenia można uruchamiać jako główne, o ile nie przechodzą z powrotem między głównym i ograniczonym kontem. Na przykład kontenery platformy Docker są domyślnie uruchamiane jako główne, więc mają tę cechę.

## <a name="global-tool-installation"></a>Instalacja narzędzia globalnego

Poniższe instrukcje przedstawiają zalecaną metodę instalowania, uruchamiania i odinstalowywania narzędzi .NET Core, które wymagają podniesionych uprawnień do wykonania.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Instalowanie narzędzia globalnego

Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj poniższe czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania tego katalogu:

- Kliknij prawym przyciskiem `%ProgramFiles%\dotnet-tools` myszy folder i wybierz polecenie **Właściwości**. Zostanie otwarte okno dialogowe **wspólne właściwości** . 
- Wybierz kartę **zabezpieczenia** . W obszarze **nazwy grup lub użytkowników**Sprawdź, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania katalogu. 
- Jeśli grupa "Użytkownicy" może zapisywać lub modyfikować katalog, użyj innej nazwy katalogu podczas instalowania narzędzi, a nie *narzędzi dotnet*.

Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień. Podczas instalacji zostanie utworzony folder *narzędzi dotnet* .

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Uruchamianie narzędzia globalnego

**Opcja 1** Użyj pełnej ścieżki z podniesionym poziomem uprawnień:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Opcja 2** Dodaj nowo utworzony folder do `%Path%`programu. Tę operację należy wykonać tylko raz.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

I uruchom z:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstaluj narzędzie globalne

W wierszu polecenia z podwyższonym poziomem uprawnień wpisz następujące polecenie:

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Narzędzia lokalne

Narzędzia lokalne są objęte zakresem drzewa dla każdego użytkownika. W przypadku korzystania z podwyższonego poziomu uprawnień narzędzia lokalne udostępniają środowisko użytkownika z ograniczeniami do środowiska z podwyższonym poziomem uprawnień. W systemie Linux i macOS w wyniku tego są ustawiane pliki z dostępem tylko do użytkownika root. Jeśli użytkownik przełączy się z powrotem do konta z ograniczeniami, użytkownik nie będzie mógł uzyskać dostępu do plików ani zapisywać do nich. Instalowanie narzędzi wymagających podniesienia uprawnień jako lokalnych narzędzi nie jest zalecane. Zamiast tego należy użyć `--tool-path` opcji i poprzednich wytycznych dla narzędzi globalnych.

## <a name="elevation-during-development"></a>Podniesienie uprawnień podczas opracowywania

Podczas programowania może być potrzebny podwyższony poziom dostępu do testowania aplikacji. Ten scenariusz jest typowy dla aplikacji IoT, na przykład. Zalecamy, aby skompilować aplikację bez podniesienia uprawnień, a następnie uruchomić ją z podniesionymi uprawnieniami. Istnieje kilka wzorców:

- Przy użyciu wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Za pomocą polecenia [dotnet Run](dotnet-run.md) z `—no-build` flagą, aby uniknąć generowania nowych plików binarnych:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Zobacz także

- [Globalne narzędzia platformy .NET Core — Omówienie](global-tools.md)
