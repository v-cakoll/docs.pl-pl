---
ms.openlocfilehash: b3bf169f60279d245568367afb0bfe004c4ebcd7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275322"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng i DSACng są po raz kolejny użyteczne w scenariuszach częściowego zaufania

|   |   |
|---|---|
|Szczegóły|CngLightup (używany w kilku apis krypto wyższego poziomu, takich jak) <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>i <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> w niektórych przypadkach polegać na pełnym zaufaniu. Należą do nich P/Invokes bez potwierdzenia <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> uprawnień <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> i ścieżki <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>kodu, gdzie ma wymagania dotyczące uprawnień dla . Począwszy od programu .NET Framework 4.6.2, CngLightup został użyty do przełączania się tam, <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> gdzie to możliwe. W rezultacie aplikacje częściowego <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> zaufania, które <xref:System.Security.SecurityException> pomyślnie używane zaczął się niepowodzeniem i zgłaszać wyjątki. Ta zmiana dodaje wymagane potwierdzenia, dzięki czemu wszystkie funkcje przy użyciu CngLightup mają wymagane uprawnienia.|
|Sugestia|Jeśli ta zmiana w .NET Framework 4.6.2 ma negatywny wpływ na aplikacje częściowego zaufania, uaktualnić do .NET Framework 4.7.1.|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
