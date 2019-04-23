---
ms.openlocfilehash: e8c48c4b1031813ce62f576e5bf1f94c082dfe4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774433"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute eksportuje zarówno jako ObsoleteAttribute i DeprecatedAttribute w scenariuszach WinMD

|   |   |
|---|---|
|Szczegóły|Podczas tworzenia biblioteki metadanych Windows (plik winmd), <xref:System.ObsoleteAttribute?displayProperty=name> atrybutu są eksportowane jako <xref:System.ObsoleteAttribute?displayProperty=name> i [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).|
|Sugestia|Ponowna kompilacja elementu istniejący kod źródłowy, który używa <xref:System.ObsoleteAttribute?displayProperty=name> atrybut może generować ostrzeżenia podczas korzystania z tego kodu z C++/CX lub JavaScript.We nie zaleca się stosowanie zarówno <xref:System.ObsoleteAttribute?displayProperty=name> i [ Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) kodem w zarządzanych zestawów; może to spowodować ostrzeżenia kompilacji.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Przekierowanie|
