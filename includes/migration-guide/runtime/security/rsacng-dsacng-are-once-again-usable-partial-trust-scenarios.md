---
ms.openlocfilehash: 8b41e3234c00059ecb5088bbf2597611d7f139b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857226"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng i DSACng są po raz kolejny użyteczne w scenariuszach częściowego zaufania

|   |   |
|---|---|
|Szczegóły|CngLightup (używany w kilku apis krypto wyższego poziomu, takich jak) <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>i <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> w niektórych przypadkach polegać na pełnym zaufaniu. Należą do nich P/Invokes bez potwierdzenia <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> uprawnień <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> i ścieżki <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>kodu, gdzie ma wymagania dotyczące uprawnień dla . Począwszy od programu .NET Framework 4.6.2, CngLightup został użyty do przełączania się tam, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> gdzie to możliwe. W rezultacie aplikacje częściowego <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> zaufania, które <xref:System.Security.SecurityException> pomyślnie używane zaczął się niepowodzeniem i zgłaszać wyjątki. Ta zmiana dodaje wymagane potwierdzenia, dzięki czemu wszystkie funkcje przy użyciu CngLightup mają wymagane uprawnienia.|
|Sugestia|Jeśli ta zmiana w .NET Framework 4.6.2 ma negatywny wpływ na aplikacje częściowego zaufania, uaktualnić do .NET Framework 4.7.1.|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
