---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449229"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Parametr logiczny elementu SignedCms. ComputeSignature jest przestrzegany

W oprogramowaniu .NET Core jest przestrzegany parametr `silent` typu Boolean metody <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>. Monit o podanie numeru PIN nie jest wyświetlany, jeśli ten parametr ma wartość `true`.

#### <a name="change-description"></a>Zmień opis

W .NET Framework parametr `silent` metody <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> jest ignorowany, a monit o podanie numeru PIN jest zawsze wyświetlany, jeśli jest to wymagane przez dostawcę. W programie .NET Core jest przestrzegany parametr `silent`, a jeśli jest ustawiony na `true`, monit o podanie numeru PIN nigdy nie jest wyświetlany, nawet jeśli jest wymagany przez dostawcę.

Obsługa komunikatów CMS/PKCS #7 została wprowadzona do programu .NET Core w wersji 2,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

2.1

#### <a name="recommended-action"></a>Zalecana akcja

Aby zapewnić, że w razie potrzeby będzie wyświetlany monit o podanie numeru PIN, aplikacje klasyczne powinny wywoływać <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> i ustawić parametr logiczny na `false`. Zachowanie rezultatowe jest takie samo jak w przypadku .NET Framework niezależnie od tego, czy kontekst dyskretny jest wyłączony.

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
