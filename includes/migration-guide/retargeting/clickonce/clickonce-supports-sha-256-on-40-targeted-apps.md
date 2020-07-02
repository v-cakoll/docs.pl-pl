---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615657"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>Technologia ClickOnce obsługuje Algorytm SHA-256 w aplikacjach przeznaczonych dla 4,0

#### <a name="details"></a>Szczegóły

Wcześniej Aplikacja ClickOnce z certyfikatem podpisanym przy użyciu algorytmu SHA-256 wymagała obecności .NET Framework 4,5 lub nowszej, nawet jeśli aplikacja skierowana do sieci 4,0. Teraz aplikacje ClickOnce w .NET Framework 4,0 mogą działać na .NET Framework 4,0, nawet jeśli są podpisane przy użyciu algorytmu SHA-256.

#### <a name="suggestion"></a>Sugestia

Ta zmiana usuwa tę zależność i zezwala na używanie certyfikatów SHA-256 do podpisywania aplikacji ClickOnce przeznaczonych dla .NET Framework 4 i wcześniejszych.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
