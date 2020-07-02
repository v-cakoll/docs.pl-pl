---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614805"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpieczenia komunikatów WCF mogą teraz korzystać z protokołów TLS 1.1 i TLS 1.2

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,7, klienci mogą skonfigurować protokół TLS 1.1 lub TLS 1.2 w zabezpieczeniach komunikatów WCF oprócz protokołów SSL 3.0 i TLS 1.0 za pośrednictwem ustawień konfiguracji aplikacji.

#### <a name="suggestion"></a>Sugestia

W .NET Framework 4,7 Obsługa protokołu TLS 1.1 i TLS 1.2 w zabezpieczeniach komunikatów WCF jest domyślnie wyłączona. Można ją włączyć, dodając następujący wiersz do `<runtime>` sekcji app.config lub web.config pliku:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |
