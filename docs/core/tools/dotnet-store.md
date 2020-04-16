---
title: Polecenie dotnet store
description: Polecenie "dotnet store" przechowuje określone zestawy w magazynie pakietów środowiska wykonawczego.
ms.date: 02/14/2020
ms.openlocfilehash: 2f28a9bc287a87f600bda385c579e8070cbaa5ab
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463386"
---
# <a name="dotnet-store"></a>dotnet store

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet store`- Przechowuje określone zestawy w [magazynie pakietów środowiska wykonawczego](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a>Opis

`dotnet store`przechowuje określone zestawy w [magazynie pakietów środowiska wykonawczego](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury. Aby uzyskać więcej informacji, zobacz temat [magazynu pakietów środowiska wykonawczego.](../deploying/runtime-store.md)

## <a name="required-options"></a>Wymagane opcje

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md). Struktura docelowa musi być określona w pliku projektu.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Plik manifestu magazynu pakietów* jest plikiem XML, który zawiera listę pakietów do przechowywania. Format pliku manifestu jest zgodny z formatem projektu w stylu SDK. Tak więc plik projektu, który odwołuje się do `-m|--manifest` żądanych pakietów może służyć z opcją do przechowywania zestawów w magazynie pakietów środowiska wykonawczego. Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku. Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identyfikator środowiska wykonawczego](../rid-catalog.md) do docelowego.

## <a name="optional-options"></a>Opcje opcjonalne

- **`--framework-version <FRAMEWORK_VERSION>`**

  Określa wersję SDK rdzenia .NET. Ta opcja umożliwia wybranie określonej wersji framework `-f|--framework` poza strukturą określoną przez tę opcję.

- **`-h|--help`**

  Pokazuje informacje o pomocy.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę do magazynu pakietów środowiska wykonawczego. Jeśli nie zostanie określony, domyślnie jest to podkatalog *magazynu* katalogu instalacyjnego profilu użytkownika .NET Core.

- **`--skip-optimization`**

  Pomija fazę optymalizacji.

- **`--skip-symbols`**

  Pomija generowanie symboli. Obecnie symbole można generować tylko w systemach Windows i Linux.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa podkatalogu *obj* bieżącego katalogu.

## <a name="examples"></a>Przykłady

- Przechowuj pakiety określone w pliku projektu *packages.csproj* dla .NET Core 2.0.0:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Przechowuj pakiety określone w *pliku packages.csproj* bez optymalizacji:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Zobacz też

- [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)
