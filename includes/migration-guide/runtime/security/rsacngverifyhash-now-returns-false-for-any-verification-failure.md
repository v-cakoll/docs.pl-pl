---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887816"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng. VerifyHash teraz zwraca wartość false dla dowolnego błędu weryfikacji

|   |   |
|---|---|
|Szczegóły|Rozpoczynając od .NET Framework 4.6.2, ta metoda zwraca **wartość false** , jeśli podpis jest nieprawidłowo sformatowany. Teraz zwraca wartość false dla dowolnego błędu weryfikacji. W .NET Framework 4,6 i 4.6.1 Metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>, jeśli podpis jest nieprawidłowo sformatowany.|
|Sugestia|Każdy kod, którego wykonywanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> należy zamiast tego wykonać, jeśli Walidacja nie powiedzie się, a metoda zwróci **wartość false**.|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
