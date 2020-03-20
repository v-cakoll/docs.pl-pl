---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997688"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikacje opublikowane za pomocą ClickOnce, które używają certyfikatu podpisywania kodu SHA-256, mogą zakończyć się niepowodzeniem w systemie Windows 2003

|   |   |
|---|---|
|Szczegóły|Plik wykonywalny jest podpisany za pomocą sha256. Wcześniej został podpisany z SHA1 niezależnie od tego, czy certyfikat podpisywania kodu był SHA-1 lub SHA-256. Dotyczy to:<ul><li>Wszystkie aplikacje utworzone za pomocą programu Visual Studio 2012 lub nowszego.</li><li>Aplikacje utworzone za pomocą programu Visual Studio 2010 lub wcześniejszych w systemach z .NET Framework 4.5 obecny.</li></ul>Ponadto jeśli .NET Framework 4.5 lub nowsze jest obecny, ClickOnce manifest jest również podpisany z SHA-256 dla certyfikatów SHA-256 niezależnie od wersji .NET Framework, dla którego został skompilowany.|
|Sugestia|Zmiana w podpisywaniu pliku wykonywalnego ClickOnce dotyczy tylko systemów Windows Server 2003; wymagają zainstalowania KB 938397. Zmiana w podpisywaniu manifestu za pomocą sha-256 nawet wtedy, gdy aplikacja jest przeznaczona dla .NET Framework 4.0 lub wcześniejszych wersji wprowadza zależność środowiska uruchomieniowego na .NET Framework 4.5 lub nowszej wersji.|
|Zakres|Brzeg|
|Wersja|4.5|
|Typ|Przekierowanie|
