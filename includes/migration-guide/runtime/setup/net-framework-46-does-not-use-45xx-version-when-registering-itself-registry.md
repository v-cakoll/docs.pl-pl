---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858487"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="3897d-101">Program .NET Framework 4.6 nie używa wersji 4.5.x.x podczas rejestrowania się w rejestrze</span><span class="sxs-lookup"><span data-stu-id="3897d-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3897d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3897d-102">Details</span></span>|<span data-ttu-id="3897d-103">Jak można się spodziewać, klucz wersji <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>ustawiony w rejestrze (at) dla .NET Framework 4.6 zaczyna się od '4.6', a nie '4.5'.</span><span class="sxs-lookup"><span data-stu-id="3897d-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="3897d-104">Aplikacje, które zależą od tych kluczy rejestru, aby wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze, powinny zostać zaktualizowane, aby zrozumieć, że 4.6 jest nową możliwą wersją i która jest zgodna z poprzednimi wersjami 4.5.x.</span><span class="sxs-lookup"><span data-stu-id="3897d-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="3897d-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3897d-105">Suggestion</span></span>|<span data-ttu-id="3897d-106">Aktualizuj aplikacje sondujące instalację programu .NET Framework 4.5, szukając kluczy rejestru 4.5, aby również zaakceptować 4.6.</span><span class="sxs-lookup"><span data-stu-id="3897d-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="3897d-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="3897d-107">Scope</span></span>|<span data-ttu-id="3897d-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="3897d-108">Edge</span></span>|
|<span data-ttu-id="3897d-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="3897d-109">Version</span></span>|<span data-ttu-id="3897d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="3897d-110">4.6</span></span>|
|<span data-ttu-id="3897d-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3897d-111">Type</span></span>|<span data-ttu-id="3897d-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3897d-112">Runtime</span></span>|
