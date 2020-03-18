---
title: polecenie dotnet store
description: Polecenie "dotnet store" przechowuje określone zestawy w magazynie pakietów w czasie wykonywania.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503579"
---
# <a name="dotnet-store"></a>dotnet store

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet store`- Przechowuje określone zestawy w [magazynie pakietów w czasie wykonywania](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a>Opis

`dotnet store`przechowuje określone zestawy w [magazynie pakietów w czasie wykonywania](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane dla docelowego czasu wykonywania i struktury. Aby uzyskać więcej informacji, zobacz temat [magazynu pakietów czasu wykonywania.](../deploying/runtime-store.md)

## <a name="required-options"></a>Wymagane opcje

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md). Platforma docelowa musi być określona w pliku projektu.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Plik manifestu magazynu pakietów* jest plikiem XML, który zawiera listę pakietów do przechowywania. Format pliku manifestu jest zgodny z formatem projektu w stylu SDK. W ten sposób plik projektu, który odwołuje `-m|--manifest` się do żądanych pakietów może służyć z opcją do przechowywania zestawów w magazynie pakietów w czasie wykonywania. Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku. Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identyfikator czasu wykonywania](../rid-catalog.md) do obiektu docelowego.

## <a name="optional-options"></a>Opcje opcjonalne

- **`--framework-version <FRAMEWORK_VERSION>`**

  Określa wersję sdk .NET Core. Ta opcja umożliwia wybranie określonej wersji framework poza `-f|--framework` ramach określonych przez opcję.

- **`-h|--help`**

  Pokazuje informacje pomocy.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę do magazynu pakietów w czasie wykonywania. Jeśli nie zostanie określony, domyślnie w podkatalogu *magazynu* katalogu instalacyjnego profilu użytkownika .NET Core.

- **`--skip-optimization`**

  Pomija fazę optymalizacji.

- **`--skip-symbols`**

  Pomija generowanie symboli. Obecnie symbole można generować tylko w systemach Windows i Linux.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa podkatalogu *obj* bieżącego katalogu.

## <a name="examples"></a>Przykłady

- Przechowywanie pakietów określonych w pliku projektu *packages.csproj* dla .NET Core 2.0.0:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Przechowuj pakiety określone w *packages.csproj* bez optymalizacji:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Zobacz też

- [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)
