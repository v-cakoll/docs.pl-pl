---
title: polecenie "isclean" dotnet
description: Polecenie "Wyczyść" programu dotnet czyści bieżący katalog.
ms.date: 06/26/2019
ms.openlocfilehash: 113bc076b9f14a471c631801fe4a7cb1e044a411
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168059"
---
# <a name="dotnet-clean"></a>dotnet clean

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet clean`-Czyści dane wyjściowe projektu.

## <a name="synopsis"></a>Streszczenie

```console
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Opis

`dotnet clean` Polecenie czyści dane wyjściowe poprzedniej kompilacji. Jest ona zaimplementowana jako [obiekt docelowy MSBuild](/visualstudio/msbuild/msbuild-targets), dlatego projekt jest oceniany, gdy polecenie jest uruchamiane. Oczyszczone zostaną tylko dane wyjściowe utworzone podczas kompilacji. Są czyszczone zarówno pośrednie (*obj*), jak i końcowe (*bin*) foldery wyjściowe.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt programu MSBuild lub rozwiązanie do czyszczenia. Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln*, i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`. Ta opcja jest wymagana tylko w przypadku czyszczenia, jeśli została określona w czasie kompilacji.

* **`-f|--framework <FRAMEWORK>`**

  [Struktura](../../standard/frameworks.md) , która została określona w czasie kompilacji. Struktura musi być zdefiniowana w [pliku projektu](csproj.md). Jeśli określono strukturę w czasie kompilacji, należy określić strukturę podczas czyszczenia.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

* **`--nologo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, który zawiera artefakty kompilacji do oczyszczenia. `-f|--framework <FRAMEWORK>` Określ przełącznik z przełącznikiem katalogu wyjściowego, jeśli określono strukturę podczas kompilowania projektu.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Czyści folder wyjściowy określonego środowiska uruchomieniowego. Ta funkcja jest używana podczas tworzenia wdrożenia z dowolnego [siebie](../deploying/index.md#self-contained-deployments-scd) . Opcja dostępna od wersji .NET Core 2,0 SDK.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości programu MSBuild. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]` Wartość domyślna to `normal`.

## <a name="examples"></a>Przykłady

* Wyczyść domyślną kompilację projektu:

  ```console
  dotnet clean
  ```

* Wyczyść projekt utworzony przy użyciu konfiguracji wydania:

  ```console
  dotnet clean --configuration Release
  ```
