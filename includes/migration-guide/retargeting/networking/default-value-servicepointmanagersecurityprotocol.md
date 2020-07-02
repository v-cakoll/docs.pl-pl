---
ms.openlocfilehash: 5c86be598ab6196ecf4da05451c7f22d2be52c12
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614699"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Wartość domyślna elementu ServicePointManager. to elementu SecurityProtocol to SecurityProtocolType.System. Wartooć

#### <a name="details"></a>Szczegóły

Począwszy od aplikacji przeznaczonych dla .NET Framework 4,7, wartość domyślna <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> Właściwości to <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> . Ta zmiana umożliwia .NET Framework interfejsów API sieci opartych na SslStream (na przykład FTP, HTTPS i SMTP) do dziedziczenia domyślnych protokołów zabezpieczeń z systemu operacyjnego zamiast przy użyciu zakodowanych wartości zdefiniowanych przez .NET Framework. Wartość domyślna zmienia się w zależności od systemu operacyjnego i dowolnej konfiguracji niestandardowej wykonywanej przez administratora systemu. Aby uzyskać informacje dotyczące domyślnego protokołu SChannel w każdej wersji systemu operacyjnego Windows, zobacz [Protokoły protokołu TLS/SSL (Dostawca SSP Schannel)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>W przypadku aplikacji przeznaczonych dla starszej wersji .NET Framework wartość domyślna <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> właściwości zależy od wersji .NET Framework docelowej. Aby uzyskać więcej informacji, zobacz [sekcję dotyczącą sieci przekierowywania zmian dotyczących migracji z .NET Framework 4.5.2 do 4,6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) .

#### <a name="suggestion"></a>Sugestia

Ta zmiana ma wpływ na aplikacje, które są przeznaczone dla .NET Framework 4,7 lub nowszych. Jeśli wolisz używać zdefiniowanego protokołu zamiast polegania na domyślnym systemie, można jawnie ustawić wartość <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> właściwości. Jeśli ta zmiana jest niepożądana, można zrezygnować z jej przez dodanie ustawienia konfiguracji do [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji. Poniższy przykład pokazuje `<runtime>` sekcję i `Switch.System.Net.DontEnableSystemDefaultTlsVersions` przełącznik rezygnacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4,7         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>
