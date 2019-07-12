---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802689"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Ulepszenia przydzielanie algorytm obszarze star wierszy siatki

|   |   |
|---|---|
|Szczegóły|Usunięto usterkę w [algorytm rozmiarów do przydzielania ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.  W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.|
|Sugestia|Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.|
|Scope|Duży|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|

