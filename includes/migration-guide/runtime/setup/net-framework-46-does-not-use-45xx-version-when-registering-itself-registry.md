---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858487"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>Program .NET Framework 4.6 nie używa wersji 4.5.x.x podczas rejestrowania się w rejestrze

|   |   |
|---|---|
|Szczegóły|Jak można się spodziewać, klucz wersji <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>ustawiony w rejestrze (at) dla .NET Framework 4.6 zaczyna się od '4.6', a nie '4.5'. Aplikacje, które zależą od tych kluczy rejestru, aby wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze, powinny zostać zaktualizowane, aby zrozumieć, że 4.6 jest nową możliwą wersją i która jest zgodna z poprzednimi wersjami 4.5.x.|
|Sugestia|Aktualizuj aplikacje sondujące instalację programu .NET Framework 4.5, szukając kluczy rejestru 4.5, aby również zaakceptować 4.6.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
