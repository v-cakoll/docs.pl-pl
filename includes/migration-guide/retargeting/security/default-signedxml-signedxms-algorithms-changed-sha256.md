---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614810"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Domyślne algorytmy SignedXML i SignedXMS zostały zmienione na SHA256

#### <a name="details"></a>Szczegóły

W .NET Framework 4,7 i starszych SignedXML i SignedCMS domyślnie SHA1 dla niektórych operacji. Począwszy od .NET Framework 4.7.1, SHA256 jest domyślnie włączone dla tych operacji. Ta zmiana jest konieczna, ponieważ algorytm SHA1 nie jest już uznawany za bezpieczny.

#### <a name="suggestion"></a>Sugestia

Istnieją dwie nowe wartości przełącznika kontekstu, które umożliwiają kontrolowanie, czy algorytm SHA1 (niezabezpieczony) lub SHA256 jest używany domyślnie:

- Switch.System.Security.Cryptography.Xml. UseInsecureHashAlgorithms
- Switch.System Security. Cryptography. PKCS. UseInsecureHashAlgorithms dla aplikacji, które są przeznaczone dla .NET Framework 4.7.1 i nowszych wersji, jeśli użycie SHA256 jest niepożądane, można przywrócić wartość domyślną SHA1, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

W przypadku aplikacji przeznaczonych dla .NET Framework 4,7 i starszych wersji można przystąpić do tej zmiany, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
