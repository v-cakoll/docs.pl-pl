---
title: polecenie dotnet clean
description: Polecenie dotnet clean czyści bieżący katalog.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503755"
---
# <a name="dotnet-clean"></a>dotnet clean

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet clean`- Czyści wyniki projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji. Jest implementowany jako [cel MSBuild,](/visualstudio/msbuild/msbuild-targets)więc projekt jest oceniany po uruchomieniu polecenia. Tylko dane wyjściowe utworzone podczas kompilacji są czyszczone. Wyczyszczone są zarówno foldery pośrednie *(obj),* jak i końcowe *(bin).*

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt MSBuild lub rozwiązanie do czyszczenia. Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln*i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie. Ta opcja jest wymagana tylko podczas czyszczenia, jeśli została określona w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Struktura,](../../standard/frameworks.md) która została określona w czasie kompilacji. Struktura musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono framework w czasie kompilacji, należy określić struktury podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od sdk .NET Core 3.0.

* **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od sdk .NET Core 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, który zawiera artefakty kompilacji do czyszczenia. Określ `-f|--framework <FRAMEWORK>` przełącznik za pomocą przełącznika katalogu wyjściowego, jeśli określono strukturę podczas budowy projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folder wyjściowy określonego czasu wykonywania. Jest to używane podczas tworzenia [samodzielnego wdrażania.](../deploying/index.md#publish-self-contained)

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości MSBuild. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartość domyślna to `normal`.

## <a name="examples"></a>Przykłady

* Wyczyść domyślną kompilację projektu:

  ```dotnetcli
  dotnet clean
  ```

* Czyszczenie projektu utworzonego przy użyciu konfiguracji wersji:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
