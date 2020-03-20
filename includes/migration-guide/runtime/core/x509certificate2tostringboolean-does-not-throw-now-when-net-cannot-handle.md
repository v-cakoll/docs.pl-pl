---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858540"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) nie zgłasza teraz, gdy .NET nie może obsłużyć certyfikatu

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5.2 i wcześniejszych wersjach ta metoda będzie zgłosić, jeśli <code>true</code> został przekazany dla parametru pełne i nie zostały zainstalowane certyfikaty, które nie były obsługiwane przez .NET Framework. Teraz metoda zakończy się pomyślnie i zwróci prawidłowy ciąg, który pomija niedostępne części certyfikatu.|
|Sugestia|Każdy kod <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> w zależności od powinny być aktualizowane, aby oczekiwać, że zwracany ciąg może wykluczyć niektóre dane certyfikatu (takie jak klucz publiczny, klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejs API wcześniej zostały zgłoszone.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
