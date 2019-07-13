---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857515"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>Jakiekolwiek niepowodzenie weryfikacji RSACng.VerifyHash teraz zwraca wartość False

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, Metoda ta zwraca <strong>False</strong> jeśli sam podpis jest źle sformatowany. Obecnie zwraca wartość false dla jakiekolwiek niepowodzenie weryfikacji. W .NET Framework 4.6 i 4.6.1, metoda zgłasza <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> jeśli sam podpis jest źle sformatowany.|
|Sugestia|Jakiegokolwiek kodu, których wykonanie zależy od obsługi <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> zamiast tego powinien zostać wykonany, jeśli weryfikacja zakończy się niepowodzeniem i metoda zwraca <strong>False</strong>.|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

