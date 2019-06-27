---
title: Podwyższonego poziomu dostępu dla polecenia dotnet
description: Poznaj najlepsze rozwiązania dla polecenia dotnet, wymagających podwyższonego poziomu dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410645"
---
# <a name="elevated-access-for-dotnet-commands"></a>Podwyższonego poziomu dostępu dla polecenia dotnet

Najlepszych praktyk tworzenia oprogramowania przewodnik deweloperów oprogramowania, wymagającego najmniejszą ilością uprawnień do zapisu. Jednak niektóre programy, takie jak narzędzia monitorowania wydajności, wymaga uprawnień administratora z powodu zasad systemu operacyjnego. Poniższe wskazówki opisano obsługiwane scenariusze dotyczące pisania oprogramowania za pomocą programu .NET Core. 

Następujące polecenia mogą być uruchamiane z podwyższonym poziomem uprawnień:

- `dotnet tool` polecenia takie jak [instalacji narzędzi dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nie zaleca się uruchamiania innych poleceń z podwyższonym poziomem uprawnień. W szczególności, nie zaleca się podniesienie uprawnień za pomocą poleceń korzystających z programu MSBuild, takich jak [dotnet restore](dotnet-restore.md), [kompilacji dotnet](dotnet-build.md), i [dotnet, uruchom](dotnet-run.md). Podstawowym problemem jest problemów z zarządzaniem uprawnieniami, gdy użytkownik przechodzi i z powrotem między głównym i ograniczeniami konta po wydaniu polecenia dotnet. Może się okazać jako użytkowników z ograniczeniami, nie masz dostępu do pliku, utworzone przez użytkownika głównego. Sposoby, aby rozwiązać ten problem, ale są one zbędne zagłębieniem się w pierwszej kolejności.

Możesz uruchamiać polecenia jako użytkownik główny, tak długo, jak nie przejścia i z powrotem między głównym i konta z ograniczeniami. Na przykład kontenery platformy Docker jako użytkownik główny domyślnie uruchamiane, dzięki czemu mają one Cecha ta.

## <a name="global-tool-installation"></a>Instalowanie narzędzi globalne

Poniższe instrukcje przedstawiają zalecaną metodą instalacji, uruchom i odinstalować narzędzia platformy .NET Core, które wymagają podniesionego poziomu uprawnień do wykonania.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Zainstaluj narzędzie globalne

Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj następujące czynności, aby sprawdzić, czy grupa "Użytkownicy", ma uprawnienia do zapisu lub modyfikowania tego katalogu:

* Kliknij prawym przyciskiem myszy `%ProgramFiles%\dotnet-tools` i wybierz polecenie **właściwości**. **Wspólne właściwości** zostanie otwarte okno dialogowe. 
* Wybierz **zabezpieczeń** kartę. W obszarze **nazwy grupy lub użytkownika**, sprawdź, czy grupa "Użytkownicy", ma uprawnienia do zapisu lub modyfikowania katalogu. 
* Jeśli grupy "Użytkownicy" można zapisać lub zmodyfikować katalogu, należy użyć nazwy z innym katalogiem podczas instalowania narzędzi zamiast *narzędzi dotnet*.

Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień. Utworzy on *narzędzi dotnet* folderu podczas instalacji.

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Uruchom narzędzie globalnej

**Opcja 1** użycie pełnej ścieżki w wierszu polecenia z podwyższonym poziomem uprawnień:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Opcja 2** Dodaj nowo utworzony folder do `%Path%`. Wystarczy wykonać tę operację na raz.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

A następnie uruchom za pomocą:

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

## <a name="local-tools"></a>Narzędzia do lokalnego

Lokalne narzędzia są w zakresie na drzewie podkatalogu dla poszczególnych użytkowników. Po uruchomieniu z podwyższonym poziomem uprawnień, lokalnego narzędzia udostępnianie środowisku użytkowników z ograniczeniami do środowiska z podniesionymi uprawnieniami. W systemie Linux i macOS powoduje to pliki, ustawiania z dostępem tylko do użytkownika głównego. Gdy użytkownik przejdzie do konta z ograniczeniami, użytkownik nie jest już można uzyskać dostęp lub zapisu do plików. Dlatego zainstalowanie narzędzi, które wymagają podniesionych uprawnień jako narzędzia do lokalnego nie jest zalecane. Zamiast tego należy użyć `--tool-path` opcja i poprzedniej wskazówki dotyczące narzędzi globalnego.

## <a name="elevation-during-development"></a>Podniesienie uprawnień w czasie projektowania

Podczas tworzenia aplikacji może być konieczne podwyższonego poziomu dostępu, aby przetestować aplikację. Ten scenariusz jest typowe w przypadku aplikacji IoT, np. Firma Microsoft zaleca tworzenie aplikacji bez podniesienia uprawnień, a następnie uruchom go z podniesionymi. Istnieje kilka wzorców w następujący sposób:

- Przy użyciu wygenerowany plik wykonywalny (zapewnia najlepszą wydajność uruchamiania):

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Za pomocą [dotnet, uruchom](dotnet-run.md) polecenia `—no-build` flagę, aby uniknąć generowania nowych danych binarnych:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Zobacz także

* [Omówienie narzędzia globalnej platformy .NET core](global-tools.md)
