---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620238"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>Element EventSource. metody WriteEvent Impls musi przekazać metody WriteEvent te same parametry, które otrzymały (plus ID)

#### <a name="details"></a>Szczegóły

Środowisko wykonawcze wymusza teraz kontrakt, który określa następujące elementy: Klasa pochodna <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> , która definiuje metodę zdarzenia ETW, musi wywołać metodę klasy bazowej <code>EventSource.WriteEvent</code> z identyfikatorem zdarzenia, po którym następują te same argumenty, które zostały przekazane przez metodę zdarzenia ETW.

#### <a name="suggestion"></a>Sugestia

<xref:System.IndexOutOfRangeException?displayProperty=fullName>Wyjątek jest generowany, jeśli <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> dane są odczytywane <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> w procesie dla źródła zdarzenia, które narusza ten kontrakt.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
