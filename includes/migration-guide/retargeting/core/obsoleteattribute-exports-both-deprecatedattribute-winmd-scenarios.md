---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616118"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttributee eksporty jako ObsoleteAttribute i DeprecatedAttribute w scenariuszach WinMD

#### <a name="details"></a>Szczegóły

Podczas tworzenia biblioteki metadanych systemu Windows (plik. winmd) ten <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybut jest eksportowany zarówno jako, jak <xref:System.ObsoleteAttribute?displayProperty=fullName> i [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).

#### <a name="suggestion"></a>Sugestia

Ponowna kompilacja istniejącego kodu źródłowego korzystającego z <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu może generować ostrzeżenia podczas korzystania z tego kodu z C++/CX lub JavaScript. nie zaleca się stosowania programów <xref:System.ObsoleteAttribute?displayProperty=fullName> i [Windows. Foundation. DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) do kodu w zarządzanych zestawach. może to spowodować wyświetlenie ostrzeżeń dotyczących kompilacji.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.5.1       |
| Typ    | Przekierowanie |
