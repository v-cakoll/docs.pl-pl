---
title: polecenie magazynu dotnet
description: Polecenie "Sklep dotnet" przechowuje określone zestawy w magazynie pakietów środowiska uruchomieniowego.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503579"
---
# <a name="dotnet-store"></a>dotnet store

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet store` — przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a>Opis

`dotnet store` przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury. Aby uzyskać więcej informacji, zobacz temat [Magazyn pakietów środowiska uruchomieniowego](../deploying/runtime-store.md) .

## <a name="required-options"></a>Wymagane opcje

- **`-f|--framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md). W pliku projektu należy określić platformę docelową.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  *Plik manifestu magazynu pakietów* to plik XML zawierający listę pakietów do przechowywania. Format pliku manifestu jest zgodny z formatem projektu w stylu zestawu SDK. Dlatego plik projektu, który odwołuje się do żądanych pakietów, może być używany z opcją `-m|--manifest`, aby przechowywać zestawy w magazynie pakietów środowiska uruchomieniowego. Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku. Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla elementu docelowego.

## <a name="optional-options"></a>Opcje opcjonalne

- **`--framework-version <FRAMEWORK_VERSION>`**

  Określa wersję zestaw .NET Core SDK. Ta opcja umożliwia wybranie określonej wersji struktury poza strukturą określoną przez opcję `-f|--framework`.

- **`-h|--help`**

  Wyświetla informacje pomocy.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Określa ścieżkę do magazynu pakietów środowiska uruchomieniowego. Jeśli nie zostanie określony, domyślnie jest to podkatalog *sklepu* w katalogu instalacyjnym programu .NET Core profilu użytkownika.

- **`--skip-optimization`**

  Pomija fazę optymalizacji.

- **`--skip-symbols`**

  Pomija generowanie symboli. Obecnie można generować tylko symbole w systemach Windows i Linux.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa podkatalogu *obj* w bieżącym katalogu.

## <a name="examples"></a>Przykłady

- Przechowuj pakiety określone w pliku projektu *Packages. csproj* dla programu .NET Core 2.0.0:

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Przechowuj pakiety określone w *Packages. csproj* bez optymalizacji:

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Zobacz też

- [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)
