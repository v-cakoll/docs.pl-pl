---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237615"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Ulepszenia przydzielanie algorytm obszarze star wierszy siatki

|   |   |
|---|---|
|Szczegóły|Usunięto usterkę w [algorytm rozmiarów do przydzielania](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) w <xref:System.Windows.Controls.Grid> wprowadzone w programie .NET Framework 4.7.  W niektórych przypadkach, takich jak siatka zawierająca <code>Height=&quot;Auto&quot;</code> zawierające pustych wierszy, wiersze zostały rozmieszczone w niewłaściwym miejscu, możliwie poza siatki całkowicie.|
|Sugestia|Aby dla aplikacji do korzystania z tych zmian należy uruchomić w .NET Framework 4.8 lub nowszym.|
|Scope|Duży|
|Wersja|4.8|
|Typ|Środowisko uruchomieniowe|
