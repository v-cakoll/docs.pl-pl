---
title: polecenie dotnet clean
description: Polecenie dotnet clean czyści bieżący katalog.
ms.date: 02/14/2020
ms.openlocfilehash: a59922feba75e940a5cee2dfeb500f4f86372870
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463700"
---
# <a name="dotnet-clean"></a>dotnet clean

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet clean`- Czyści wyniki projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji. Jest implementowany jako [obiekt docelowy MSBuild,](/visualstudio/msbuild/msbuild-targets)więc projekt jest oceniany po uruchomieniu polecenia. Tylko dane wyjściowe utworzone podczas kompilacji są czyszczone. Czyszczone są zarówno foldery pośrednie (*obj)* jak i końcowe wyjście *(bin).*

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt LUB rozwiązanie MSBuild do czyszczenia. Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się *proj* lub *sln*i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie. Ta opcja jest wymagana tylko podczas czyszczenia, jeśli określono ją w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Struktura,](../../standard/frameworks.md) która została określona w czasie kompilacji. Struktura musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono strukturę w czasie kompilacji, należy określić strukturę podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od .NET Core 3.0 SDK.

* **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od .NET Core 3.0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, który zawiera artefakty kompilacji do czyszczenia. Określ `-f|--framework <FRAMEWORK>` przełącznik z przełącznikiem katalogu wyjściowego, jeśli określono strukturę podczas budowy projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folder wyjściowy określonego środowiska uruchomieniowego. Jest to używane podczas tworzenia [samodzielnego wdrożenia.](../deploying/index.md#publish-self-contained)

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości MSBuild. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartość domyślna to `normal`.

## <a name="examples"></a>Przykłady

* Czyszczenie domyślnej kompilacji projektu:

  ```dotnetcli
  dotnet clean
  ```

* Czyszczenie projektu utworzonego przy użyciu konfiguracji release:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
