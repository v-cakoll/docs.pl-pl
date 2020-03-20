---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237615"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Ulepszenia algorytmu przydzielania miejsca w wierszach gwiazd siatki

|   |   |
|---|---|
|Szczegóły|Naprawiono błąd w [algorytmie przydzielania rozmiarów do)](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)w wprowadzonym <xref:System.Windows.Controls.Grid> w .NET Framework 4.7.  W niektórych przypadkach, takich <code>Height=&quot;Auto&quot;</code> jak Grid z zawierającym puste wiersze, wiersze zostały rozmieszczone w niewłaściwym położeniu, prawdopodobnie poza Grid całkowicie.|
|Sugestia|Aby aplikacja korzystać z tych zmian, należy uruchomić na .NET Framework 4.8 lub nowszych.|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
