---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615659"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Aplikacje opublikowane przy użyciu technologii ClickOnce wykorzystującej certyfikat podpisywania kodu SHA-256 mogą kończyć się niepowodzeniem w systemie Windows 2003

#### <a name="details"></a>Szczegóły

Plik wykonywalny jest podpisany za pomocą SHA256. Wcześniej było podpisane przy użyciu algorytmu SHA1, niezależnie od tego, czy certyfikat podpisywania kodu był algorytmem SHA-1 lub SHA-256. Dotyczy to:

- Wszystkie aplikacje skompilowane przy użyciu programu Visual Studio 2012 lub nowszego.
- Aplikacje skompilowane przy użyciu programu Visual Studio 2010 lub starszej wersji w systemach z .NET Framework 4,5.
Ponadto jeśli jest obecny .NET Framework 4,5 lub nowszy, manifest ClickOnce jest również podpisany przy użyciu algorytmu SHA-256 dla certyfikatów SHA-256 niezależnie od wersji .NET Framework, z którą została skompilowana.

#### <a name="suggestion"></a>Sugestia

Zmiana podczas podpisywania pliku wykonywalnego ClickOnce dotyczy tylko systemów Windows Server 2003; wymagają one zainstalowania KB 938397. Zmiana podczas podpisywania manifestu z algorytmem SHA-256 nawet wtedy, gdy aplikacja jest przeznaczona dla .NET Framework 4,0 lub wcześniejszych wersji wprowadza zależność środowiska uruchomieniowego na .NET Framework 4,5 lub nowszej wersji.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.5         |
| Typ    | Przekierowanie |
