---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721202"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>Parametr logiczny elementu SignedCms. ComputeSignature jest przestrzegany

W programie .NET Core `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> jest przestrzegany parametr Boolean metody. Monit o podanie numeru PIN nie jest wyświetlany, jeśli ten parametr jest ustawiony na `true` .

#### <a name="change-description"></a>Zmień opis

W .NET Framework `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody jest ignorowany, a monit o podanie numeru PIN jest zawsze wyświetlany, jeśli jest to wymagane przez dostawcę. W przypadku platformy .NET Core `silent` parametr jest przestrzegany, a w przypadku ustawienia opcji monit o podanie `true` numeru PIN nigdy nie jest wyświetlany, nawet jeśli jest wymagany przez dostawcę.

Obsługa komunikatów CMS/PKCS #7 została wprowadzona do programu .NET Core w wersji 2,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

2.1

#### <a name="recommended-action"></a>Zalecana akcja

Aby zapewnić, że w razie potrzeby będzie wyświetlany monit o podanie numeru PIN, aplikacje klasyczne powinny wywołać <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> i ustawić parametr logiczny `false` . Zachowanie rezultatowe jest takie samo jak w przypadku .NET Framework niezależnie od tego, czy kontekst dyskretny jest wyłączony.

#### <a name="category"></a>Kategoria

Kryptografia

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
