---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887816"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash zwraca teraz False dla każdego błędu weryfikacji

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, ta metoda zwraca **False,** jeśli sam podpis jest źle sformatowany. Teraz zwraca false dla każdego błędu weryfikacji. W .NET Framework 4.6 i 4.6.1 metoda <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zgłasza, jeśli podpis sam jest źle sformatowany.|
|Sugestia|Każdy kod, którego wykonanie <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zależy od obsługi należy wykonać zamiast tego, jeśli sprawdzanie poprawności nie powiedzie się, a metoda zwraca **False**.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
