---
title: polecenie magazynu DotNet
description: "Polecenie \"dotnet magazynu\" przechowuje określonych zestawów w magazynie pakietów środowiska wykonawczego."
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: c8e09141eebef2cbddf6742cceeff05e11c25adf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-store"></a>Magazyn DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nazwa

`dotnet store`-Przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).

## <a name="synopsis"></a>Streszczenie

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Opis

`dotnet store`przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md). Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i framework. Aby uzyskać więcej informacji, zobacz [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md) tematu.

## <a name="required-options"></a>Wymagane opcje

`-f|--framework <FRAMEWORK>`

Określa [platformy docelowej](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

*Pliku manifestu sklepu pakietu* jest plik XML, który zawiera listę pakietów do przechowywania. Format pliku manifestu jest zgodny z *csproj* format. Tak *csproj* pliku projektu, który odwołuje się do żądanego pakietów można używać z `-m|--manifest` umożliwia przechowywanie zestawów w magazynie pakietów środowiska wykonawczego. Aby określić wiele plików manifestu, należy powtórzyć dla każdego pliku opcji i ścieżka: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Identyfikator środowiska uruchomieniowego do obiektu docelowego.

## <a name="optional-options"></a>Dodatkowe opcje

`--framework-version <FRAMEWORK_VERSION>`

Określa wersję zestawu SDK programu .NET Core. Ta opcja umożliwia wybranie określonych framework w wersji poza framework określona przez `-f|--framework` opcji.

`-h|--help`

Pokazuje informacje pomocy.

`-o|--output <OUTPUT_DIRECTORY>`

Określa ścieżkę do magazynu pakiet środowiska wykonawczego. Jeśli nie zostanie określony, domyślnie *przechowywania* podkatalogu w katalogu instalacji platformy .NET Core profilu użytkownika.

`--skip-optimization`

Pomija fazy optymalizacji.

`--skip-symbols`

Pomija Generowanie symboli. Obecnie można generować tylko symbole w systemach Windows i Linux.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Katalog roboczy używany przez polecenie. Jeśli nie zostanie określony, używa *obj* podkatalog bieżącego katalogu.

## <a name="examples"></a>Przykłady

Przechowywania pakietów określone w *packages.csproj* pliku projektu dla platformy .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Przechowywania pakietów określone w *packages.csproj* bez optymalizacji:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Zobacz także

[Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md)   
