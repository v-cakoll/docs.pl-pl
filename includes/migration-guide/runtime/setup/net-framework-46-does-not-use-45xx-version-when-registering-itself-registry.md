---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664478"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="975f5-101">.NET Framework 4.6 nie korzystają z wersji 4.5.x.x po zarejestrowaniu się w rejestrze</span><span class="sxs-lookup"><span data-stu-id="975f5-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="975f5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="975f5-102">Details</span></span>|<span data-ttu-id="975f5-103">Jak można oczekiwać, że, klucz wersji ustawiony w rejestrze (w <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) dla programu .NET Framework 4.6 zaczyna się od "4.6", nie 4.5.</span><span class="sxs-lookup"><span data-stu-id="975f5-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="975f5-104">Aplikacje, które są zależne od tych kluczy rejestru, aby dowiedzieć się, które wersje .NET Framework są zainstalowane na maszynie powinien zostać zaktualizowany, aby zrozumieć, 4.6 jest nowa wersja możliwe i taki, który jest zgodny z 4.5.x poprzednie wersje.</span><span class="sxs-lookup"><span data-stu-id="975f5-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="975f5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="975f5-105">Suggestion</span></span>|<span data-ttu-id="975f5-106">Aktualizuj aplikacje sondowania dla .NET Framework 4.5 Zainstaluj, wyszukując 4.5 klucze rejestru, aby także zaakceptować 4.6.</span><span class="sxs-lookup"><span data-stu-id="975f5-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="975f5-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="975f5-107">Scope</span></span>|<span data-ttu-id="975f5-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="975f5-108">Edge</span></span>|
|<span data-ttu-id="975f5-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="975f5-109">Version</span></span>|<span data-ttu-id="975f5-110">4.6</span><span class="sxs-lookup"><span data-stu-id="975f5-110">4.6</span></span>|
|<span data-ttu-id="975f5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="975f5-111">Type</span></span>|<span data-ttu-id="975f5-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="975f5-112">Runtime</span></span>|
