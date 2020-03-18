---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449229"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Przestrzegany jest parametr logiczny podpisu SignedCms.ComputeSignature

W .NET Core jest `silent` przestrzegana <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametr logiczny metody. Monit o numer PIN nie `true`jest wyświetlany, jeśli ten parametr jest ustawiony na .

#### <a name="change-description"></a>Zmień opis

W platformie .NET `silent` Framework <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametr metody jest ignorowany, a monit o numer PIN jest zawsze wyświetlany, jeśli jest wymagany przez dostawcę. W .NET Core `silent` parametr jest przestrzegany, `true`a jeśli jest ustawiona na , wiersz pin nigdy nie jest wyświetlany, nawet jeśli jest to wymagane przez dostawcę.

Obsługa komunikatów #7 CMS/PKCS została wprowadzona do programu .NET Core w wersji 2.1.

#### <a name="version-introduced"></a>Wprowadzona wersja

2.1

#### <a name="recommended-action"></a>Zalecana akcja

Aby upewnić się, że w razie potrzeby <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> pojawi się monit o numer PIN, aplikacje klasyczne powinny wywołać i ustawić parametr Logiczny na `false`. Wynikowe zachowanie jest taka sama jak w .NET Framework niezależnie od tego, czy kontekst cichy jest tam wyłączony.

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
