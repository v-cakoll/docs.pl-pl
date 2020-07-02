---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621205"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng. VerifyHash teraz zwraca wartość false dla dowolnego błędu weryfikacji

#### <a name="details"></a>Szczegóły

Rozpoczynając od .NET Framework 4.6.2, ta metoda zwraca **wartość false** , jeśli podpis jest nieprawidłowo sformatowany. Teraz zwraca wartość false dla dowolnego błędu weryfikacji. W .NET Framework 4,6 i 4.6.1 Metoda zgłasza, <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> Jeśli podpis jest nieprawidłowo sformatowany.

#### <a name="suggestion"></a>Sugestia

Każdy kod, którego wykonywanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> należy zamiast tego wykonać, jeśli Walidacja nie powiedzie się, a metoda zwraca **wartość false**.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
