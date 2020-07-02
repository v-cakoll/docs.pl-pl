---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620227"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Odbiornika obcina ciągi z osadzonymi wartościami null

#### <a name="details"></a>Szczegóły

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>obcina ciągi z osadzonymi wartościami null. Klasa nie obsługuje znaków o wartości null <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Zmiana ta dotyczy tylko aplikacji, które używają <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> do odczytu <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> danych w procesie i używania znaków null jako ograniczników.

#### <a name="suggestion"></a>Sugestia

<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>dane powinny być aktualizowane, jeśli jest to możliwe, nie mogą być używane w osadzonych znakach null.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
