---
ms.openlocfilehash: c20d5fb3d700ba7649e423a79e4598b327c50a00
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622264"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Niepoprawna generacja kodu podczas przekazywania i porównywania wartości UInt16

#### <a name="details"></a>Szczegóły

Ze względu na zmiany wprowadzone w .NET Framework 4,7, w niektórych przypadkach kod wygenerowany przez kompilator JIT w aplikacjach uruchomionych na .NET Framework 4,7 niepoprawnie porównuje dwie <code>T:System.UInt16</code> wartości. Aby uzyskać więcej informacji, zobacz temat [#11508 problemu: ciche złe codegen podczas przekazywania i porównywania argumentów UShort](https://github.com/dotnet/coreclr/issues/11508) na GitHub.com.

#### <a name="suggestion"></a>Sugestia

Jeśli wystąpią problemy z porównaniem 16-bitowych wartości unsigned w .NET Framework 4,7, należy przeprowadzić uaktualnienie do .NET Framework 4.7.1.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe|
