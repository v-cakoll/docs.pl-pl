---
ms.openlocfilehash: 242a9952cb47d170aceffa1aa392071eb40cc6ab
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857226"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng i DSACng są ponownie użyteczne w sytuacjach częściowego zaufania

|   |   |
|---|---|
|Szczegóły|CngLightup (używana w kilku wyższego poziomu szyfrowania interfejsów API, takich jak <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) i <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> w niektórych przypadkach zależą od pełnego zaufania. Obejmują one P/Invokes bez potwierdzające <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> uprawnienia i ścieżek kodu gdzie <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> ma zapotrzebowanie uprawnień dla <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType>. Począwszy od programu .NET Framework 4.6.2, aby przełączyć się do użyto CngLightup <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> wszędzie tam, gdzie to możliwe. W rezultacie aplikacje częściowej relacji zaufania, ona pomyślnie użyta <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> rozpoczęła się nie powieść i zgłosić <xref:System.Security.SecurityException> wyjątków. Ta zmiana dodaje wymagane potwierdza, tak aby wszystkie funkcje za pomocą CngLightup wymaganych uprawnień.|
|Sugestia|Jeśli ta zmiana w programie .NET Framework 4.6.2 ma negatywnego wpływu na Twoje aplikacje częściowej relacji zaufania, uaktualnienie do programu .NET Framework 4.7.1.|
|Scope|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

