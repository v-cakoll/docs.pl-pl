---
title: polecenie magazynu dotnet
description: Polecenie "Sklep dotnet" przechowuje określone zestawy w magazynie pakietów środowiska uruchomieniowego.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733055"
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nazwa

`dotnet store` — przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Opis

`dotnet store` przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury. Aby uzyskać więcej informacji, zobacz temat [Magazyn pakietów środowiska uruchomieniowego](../deploying/runtime-store.md) .

## <a name="required-options"></a>Wymagane opcje

`-f|--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Plik manifestu magazynu pakietów* to plik XML zawierający listę pakietów do przechowywania. Format pliku manifestu jest zgodny z formatem projektu w stylu zestawu SDK. Dlatego plik projektu, który odwołuje się do żądanych pakietów, może być używany z opcją `-m|--manifest`, aby przechowywać zestawy w magazynie pakietów środowiska uruchomieniowego. Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku. Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla elementu docelowego.

## <a name="optional-options"></a>Opcje opcjonalne

`--framework-version <FRAMEWORK_VERSION>`

Określa wersję zestaw .NET Core SDK. Ta opcja umożliwia wybranie określonej wersji struktury poza strukturą określoną przez opcję `-f|--framework`.

`-h|--help`

Wyświetla informacje pomocy.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do magazynu pakietów środowiska uruchomieniowego. Jeśli nie zostanie określony, domyślnie jest to podkatalog *sklepu* w katalogu instalacyjnym programu .NET Core profilu użytkownika.

`--skip-optimization`

Pomija fazę optymalizacji.

`--skip-symbols`

Pomija generowanie symboli. Obecnie można generować tylko symbole w systemach Windows i Linux.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa podkatalogu *obj* w bieżącym katalogu.

## <a name="examples"></a>Przykłady

Przechowuj pakiety określone w pliku projektu *Packages. csproj* dla programu .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Przechowuj pakiety określone w *Packages. csproj* bez optymalizacji:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Zobacz także

- [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)
