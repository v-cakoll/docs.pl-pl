---
title: polecenie magazynu DotNet
description: Polecenie "dotnet magazynu" są przechowywane w określonych zestawach w Magazyn pakietu środowiska uruchomieniowego.
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a12738d0cc8edcbb65d5b6fab6e7c8b209b0f4b5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032361"
---
# <a name="dotnet-store"></a>Magazyn DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nazwa

`dotnet store` -Zapisuje określone zestawy w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Opis

`dotnet store` zapisuje określone zestawy w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane pod kątem docelowe środowisko uruchomieniowe i struktury. Aby uzyskać więcej informacji, zobacz [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md) tematu.

## <a name="required-options"></a>Wymagane opcje

`-f|--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Pliku manifestu sklepu pakietu* jest plikiem XML, który zawiera listę pakietów do przechowywania. Format pliku manifestu jest zgodny z formatem projekt zestawu SDK stylu. Tak, plik projektu, który odwołuje się odpowiednie pakiety można łączyć z `-m|--manifest` opcję przechowywania zestawów w Magazyn pakietu środowiska uruchomieniowego. Do określenia wielu plików manifestu, należy powtórzyć opcji i ścieżki dla każdego pliku. Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) do obiektu docelowego.

## <a name="optional-options"></a>Dodatkowe opcje

`--framework-version <FRAMEWORK_VERSION>`

Określa wersję zestawu .NET Core SDK. Ta opcja umożliwia wybranie określonych framework w wersji poza ramy określony przez `-f|--framework` opcji.

`-h|--help`

Pokazuje informacje pomocy.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do Magazyn pakietu środowiska uruchomieniowego. Jeśli nie zostanie określony, jego wartość domyślna to *przechowywania* podkatalogu katalogu instalacji platformy .NET Core w profilu użytkownika.

`--skip-optimization`

Pomija faza optymalizacji.

`--skip-symbols`

Pomija symbolu generacji. Obecnie możesz tylko wygenerować symbole w systemach Windows i Linux.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa *obj* podkatalogiem bieżącego katalogu.

## <a name="examples"></a>Przykłady

Store pakiety określone w *packages.csproj* pliku projektu dla platformy .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Store pakiety określone w *packages.csproj* bez optymalizacji:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Zobacz także

* [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)