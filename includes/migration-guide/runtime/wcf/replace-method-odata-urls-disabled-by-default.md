---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620388"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Metoda replace w adresach URL usługi OData jest domyślnie wyłączona

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, Metoda replace w adresach URL usługi OData jest domyślnie wyłączona. Gdy funkcja zamiany OData jest wyłączona (teraz domyślnie), wszelkie żądania użytkowników, w tym funkcje Replace (rzadko występujące), zakończą się niepowodzeniem.

#### <a name="suggestion"></a>Sugestia

Jeśli Metoda replace jest wymagana (co jest nietypowe), można ją zmienić za pomocą ustawień konfiguracji ( <xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName> ). Jednak włączona Metoda replace może otwierać luki w zabezpieczeniach i być używana tylko po dokładnym przeglądzie.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
