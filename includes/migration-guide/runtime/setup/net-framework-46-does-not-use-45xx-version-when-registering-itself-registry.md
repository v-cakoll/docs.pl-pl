---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621325"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>W .NET Framework 4,6 nie jest używana wersja 4.5. x. x podczas rejestrowania się w rejestrze

#### <a name="details"></a>Szczegóły

Ponieważ jeden z nich może oczekiwać, klucz wersji ustawiony w rejestrze (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> ) dla .NET Framework 4,6 rozpoczyna się od "4,6", a nie "4,5". Aplikacje, które są zależne od tych kluczy rejestru, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze, należy zaktualizować, aby zrozumieć, że 4,6 to nowa możliwa wersja i taka, która jest zgodna z poprzednimi wersjami 4.5. x.

#### <a name="suggestion"></a>Sugestia

Zaktualizuj aplikacje sondowania dla .NET Framework 4,5, wyszukując klucze rejestru 4,5, aby akceptować 4,6.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
