---
ms.openlocfilehash: da79a19b3276f6fd2d679eb98406dd85e2a19948
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997688"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikacje opublikowane przy użyciu technologii ClickOnce wykorzystującej certyfikat podpisywania kodu SHA-256 mogą kończyć się niepowodzeniem w systemie Windows 2003

|   |   |
|---|---|
|Szczegóły|Plik wykonywalny jest podpisany za pomocą SHA256. Wcześniej było podpisane przy użyciu algorytmu SHA1, niezależnie od tego, czy certyfikat podpisywania kodu był algorytmem SHA-1 lub SHA-256. Dotyczy to:<ul><li>Wszystkie aplikacje skompilowane przy użyciu programu Visual Studio 2012 lub nowszego.</li><li>Aplikacje skompilowane przy użyciu programu Visual Studio 2010 lub starszej wersji w systemach z .NET Framework 4,5.</li></ul>Ponadto jeśli jest obecny .NET Framework 4,5 lub nowszy, manifest ClickOnce jest również podpisany przy użyciu algorytmu SHA-256 dla certyfikatów SHA-256 niezależnie od wersji .NET Framework, z którą została skompilowana.|
|Sugestia|Zmiana podczas podpisywania pliku wykonywalnego ClickOnce dotyczy tylko systemów Windows Server 2003; wymagają one zainstalowania KB 938397. Zmiana podczas podpisywania manifestu z algorytmem SHA-256 nawet wtedy, gdy aplikacja jest przeznaczona dla .NET Framework 4,0 lub wcześniejszych wersji wprowadza zależność środowiska uruchomieniowego na .NET Framework 4,5 lub nowszej wersji.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Przekierowanie|
