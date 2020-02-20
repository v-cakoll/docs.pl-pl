---
title: polecenie "isclean" dotnet
description: Polecenie "Wyczyść" programu dotnet czyści bieżący katalog.
ms.date: 06/26/2019
ms.openlocfilehash: 715a33a8a1aa13a2a76f9d4522413dcc72e4b4aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451359"
---
# <a name="dotnet-clean"></a>dotnet clean

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name (Nazwa)

`dotnet clean` — czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji. Jest ona zaimplementowana jako [obiekt docelowy MSBuild](/visualstudio/msbuild/msbuild-targets), dlatego projekt jest oceniany, gdy polecenie jest uruchamiane. Oczyszczone zostaną tylko dane wyjściowe utworzone podczas kompilacji. Są czyszczone zarówno pośrednie (*obj*), jak i końcowe (*bin*) foldery wyjściowe.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt programu MSBuild lub rozwiązanie do czyszczenia. Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln*, i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartością domyślną jest `Debug`. Ta opcja jest wymagana tylko w przypadku czyszczenia, jeśli została określona w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Struktura](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono strukturę w czasie kompilacji, należy określić strukturę podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

* **`--nologo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, który zawiera artefakty kompilacji do oczyszczenia. Określ przełącznik `-f|--framework <FRAMEWORK>` z przełącznikiem katalogu wyjściowego, jeśli określono strukturę podczas kompilowania projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folder wyjściowy określonego środowiska uruchomieniowego. Ta funkcja jest używana podczas tworzenia wdrożenia z dowolnego [siebie](../deploying/index.md#publish-self-contained) . Opcja dostępna od wersji .NET Core 2,0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości programu MSBuild. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `normal`.

## <a name="examples"></a>Przykłady

* Wyczyść domyślną kompilację projektu:

  ```dotnetcli
  dotnet clean
  ```

* Wyczyść projekt utworzony przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet clean --configuration Release
  ```
