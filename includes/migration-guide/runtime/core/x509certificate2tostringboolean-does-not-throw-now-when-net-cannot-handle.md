---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621322"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2. ToString (wartość logiczna) nie jest teraz zgłaszana, gdy platforma .NET nie może obsłużyć certyfikatu

#### <a name="details"></a>Szczegóły

W .NET Framework 4.5.2 i starszych wersjach ta metoda zostałaby <code>true</code> zgłoszona, jeśli została przeniesiona do parametru verbose i zainstalowano certyfikaty, które nie były obsługiwane przez .NET Framework. Teraz Metoda zakończy się pomyślnie i zwróci prawidłowy ciąg, który pomija niedostępne fragmenty certyfikatu.

#### <a name="suggestion"></a>Sugestia

Każdy kod w zależności od tego <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> należy zaktualizować, aby oczekiwać, że zwrócony ciąg może wykluczyć niektóre dane certyfikatu (takie jak klucz publiczny, klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejs API zostałby wcześniej wygenerowany.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
