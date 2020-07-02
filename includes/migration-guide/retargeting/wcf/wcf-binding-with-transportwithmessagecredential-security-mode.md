---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614730"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Powiązanie WCF z trybem zabezpieczeń TransportWithMessageCredential

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.6.1, powiązanie WCF korzystające z trybu zabezpieczeń TransportWithMessageCredential można skonfigurować do odbierania komunikatów z niepodpisanymi &quot; do &quot; nagłówków kluczy zabezpieczeń asymetrycznych. Domyślnie niepodpisane &quot; do &quot; nagłówków nadal będą odrzucane w .NET Framework 4.6.1. Zostaną one zaakceptowane tylko wtedy, gdy aplikacja zdecyduje się na ten nowy tryb operacji za pomocą Switch.System. Element ServiceModel. AllowUnsignedToHeader Configuration Switch.

#### <a name="suggestion"></a>Sugestia

Ponieważ jest to funkcja opcjonalna, nie powinna mieć wpływu na zachowanie istniejących aplikacji.<br/>Aby kontrolować, czy nowe zachowanie jest używane, użyj następującego ustawienia konfiguracji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Przezroczyste |
| Wersja | 4.6.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
