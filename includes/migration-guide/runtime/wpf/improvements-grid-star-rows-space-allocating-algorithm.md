---
ms.openlocfilehash: bd3b1cc6a98f01d8c40b4cd67002e79a2c4fe714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665706"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Ulepszenia przydzielanie algorytm obszarze star wierszy siatki

|   |   |
|---|---|
|Szczegóły|Usunięto usterkę w [algorytm rozmiarów do przydzielania *-wierszy](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.  W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.|
|Sugestia|Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
