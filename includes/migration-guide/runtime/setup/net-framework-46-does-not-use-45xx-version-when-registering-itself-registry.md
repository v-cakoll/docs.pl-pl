---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621325"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="cb082-101">W .NET Framework 4,6 nie jest używana wersja 4.5. x. x podczas rejestrowania się w rejestrze</span><span class="sxs-lookup"><span data-stu-id="cb082-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="cb082-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cb082-102">Details</span></span>

<span data-ttu-id="cb082-103">Ponieważ jeden z nich może oczekiwać, klucz wersji ustawiony w rejestrze (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> ) dla .NET Framework 4,6 rozpoczyna się od "4,6", a nie "4,5".</span><span class="sxs-lookup"><span data-stu-id="cb082-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="cb082-104">Aplikacje, które są zależne od tych kluczy rejestru, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze, należy zaktualizować, aby zrozumieć, że 4,6 to nowa możliwa wersja i taka, która jest zgodna z poprzednimi wersjami 4.5. x.</span><span class="sxs-lookup"><span data-stu-id="cb082-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cb082-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cb082-105">Suggestion</span></span>

<span data-ttu-id="cb082-106">Zaktualizuj aplikacje sondowania dla .NET Framework 4,5, wyszukując klucze rejestru 4,5, aby akceptować 4,6.</span><span class="sxs-lookup"><span data-stu-id="cb082-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="cb082-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cb082-107">Name</span></span>    | <span data-ttu-id="cb082-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="cb082-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cb082-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="cb082-109">Scope</span></span>   |<span data-ttu-id="cb082-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="cb082-110">Edge</span></span>|
|<span data-ttu-id="cb082-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="cb082-111">Version</span></span>|<span data-ttu-id="cb082-112">4.6</span><span class="sxs-lookup"><span data-stu-id="cb082-112">4.6</span></span>|
|<span data-ttu-id="cb082-113">Typ</span><span class="sxs-lookup"><span data-stu-id="cb082-113">Type</span></span>|<span data-ttu-id="cb082-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cb082-114">Runtime</span></span>|
