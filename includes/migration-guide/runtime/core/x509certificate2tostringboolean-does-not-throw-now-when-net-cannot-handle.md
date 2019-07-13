---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858540"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.toString(Boolean) throw, kiedy .NET nie obsługuje teraz certyfikatu

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5.2 i wcześniejszych wersjach, ta metoda zgłasza, jeśli <code>true</code> została przekazana dla parametru verbose i zostały zainstalowane certyfikaty, które nie były obsługiwane przez .NET Framework. Teraz metoda powiedzie się i zwraca prawidłowy ciąg, które pomija niedostępny części certyfikatu.|
|Sugestia|Każdy kod w zależności od <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> powinny być aktualizowane można oczekiwać, że zwrócony ciąg mogą wyłączyć niektórych danych certyfikatu (na przykład klucz publiczny klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejsu API będzie mieć wcześniej wygenerowany.|
|Scope|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

