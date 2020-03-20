---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802449"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Niepoprawne generowanie kodu podczas przekazywania i porównywania wartości UInt16

|   |   |
|---|---|
|Szczegóły|Ze względu na zmiany wprowadzone w programie .NET Framework 4.7, w niektórych przypadkach kod wygenerowany przez kompilator JIT w aplikacjach uruchomionych w programie .NET Framework 4.7 niepoprawnie porównuje dwie <code>T:System.UInt16</code> wartości. Aby uzyskać więcej informacji, zobacz [#11508 problem: Silent bad codegen podczas przekazywania i porównywania argumentów ushort](https://github.com/dotnet/coreclr/issues/11508) na GitHub.com.|
|Sugestia|Jeśli wystąpią problemy w porównaniu 16-bitowych niepodpisanych wartości w .NET Framework 4.7, uaktualnij do programu .NET Framework 4.7.1.|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
