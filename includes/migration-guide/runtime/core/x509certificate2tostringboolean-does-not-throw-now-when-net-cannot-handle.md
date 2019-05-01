---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664509"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.toString(Boolean) throw, kiedy .NET nie obsługuje teraz certyfikatu

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5.2 i wcześniejszych wersjach, ta metoda zgłasza, jeśli <code>true</code> została przekazana dla parametru verbose i zostały zainstalowane certyfikaty, które nie były obsługiwane przez .NET Framework. Teraz metoda powiedzie się i zwraca prawidłowy ciąg, które pomija niedostępny części certyfikatu.|
|Sugestia|Każdy kod w zależności od <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> powinny być aktualizowane można oczekiwać, że zwrócony ciąg mogą wyłączyć niektórych danych certyfikatu (na przykład klucz publiczny klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejsu API będzie mieć wcześniej wygenerowany.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
