---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620173"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Udostępnianie stanu sesji przy użyciu Asp.Net StateServer wymaga, aby wszystkie serwery w kolektywie serwerów sieci Web używały tej samej wersji .NET Framework

#### <a name="details"></a>Szczegóły

Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> stanu sesji wszystkie serwery w danej farmie sieci Web muszą używać tej samej wersji .NET Framework, aby zapewnić prawidłowe udostępnianie stanu.

#### <a name="suggestion"></a>Sugestia

Pamiętaj, aby uaktualnić .NET Framework wersje na serwerach sieci Web, które udostępniają stan w tym samym czasie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
