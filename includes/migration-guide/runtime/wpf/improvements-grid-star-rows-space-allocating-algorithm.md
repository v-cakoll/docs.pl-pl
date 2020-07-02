---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622096"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Ulepszenia siatki z gwiazdkami — przydzielenie algorytmu w przestrzeni wierszy

#### <a name="details"></a>Szczegóły

Rozwiązano usterkę w [algorytmie przydzielania rozmiarów do](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)programu w ramach <xref:System.Windows.Controls.Grid> wprowadzenia w .NET Framework 4,7.  W niektórych przypadkach, takich jak siatka <code>Height=&quot;Auto&quot;</code> zawierająca puste wiersze, wiersze były ułożone w niewłaściwej pozycji, prawdopodobnie poza siatką.

#### <a name="suggestion"></a>Sugestia

Aby aplikacja mogła korzystać z tych zmian, należy ją uruchomić w .NET Framework 4,8 lub nowszej.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4,8|
|Typ|Środowisko uruchomieniowe|
