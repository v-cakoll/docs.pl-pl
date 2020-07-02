---
ms.openlocfilehash: e92cbb7decb5e530bbf611cec26ce03a05e06eb3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622265"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng i DSACng są ponownie nadające się do użytku w scenariuszach częściowej relacji zaufania

#### <a name="details"></a>Szczegóły

CngLightup (używany w kilku interfejsów API kryptografii wyższego poziomu, takich jak <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> ), a <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> w niektórych przypadkach polega na pełnym zaufaniu. Obejmują one polecenie P/Invoke bez potwierdzeń <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> i ścieżki kodu, <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> w których istnieją żądania dotyczące uprawnień <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> . Począwszy od .NET Framework 4.6.2, CngLightup został użyty do przełączenia do <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wszędzie tam, gdzie to możliwe. W związku z tym częściowo zaufane aplikacje, które pomyślnie używały, <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> zaczęły kończyć się niepowodzeniem i generować <xref:System.Security.SecurityException> wyjątki. Ta zmiana powoduje dodanie wymaganych potwierdzeń, aby wszystkie funkcje korzystające z CngLightup miały wymagane uprawnienia.

#### <a name="suggestion"></a>Sugestia

Jeśli ta zmiana w .NET Framework 4.6.2 ma negatywny wpływ na aplikacje częściowej relacji zaufania, przeprowadź uaktualnienie do .NET Framework 4.7.1.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
