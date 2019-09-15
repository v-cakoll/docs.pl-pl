---
title: Umieszczanie zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971637"
---
# <a name="assembly-placement"></a><span data-ttu-id="90c7a-102">Umieszczanie zestawu</span><span class="sxs-lookup"><span data-stu-id="90c7a-102">Assembly Placement</span></span>
<span data-ttu-id="90c7a-103">W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony).</span><span class="sxs-lookup"><span data-stu-id="90c7a-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="90c7a-104">Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<kodu bazowej >](../../framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="90c7a-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="90c7a-105">Jeśli zestaw nie ma silnej nazwy, lokalizacja określona przy użyciu [ \<bazowej kodu > element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) jest ograniczone do katalogu aplikacji lub podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="90c7a-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="90c7a-106">Jeśli zestaw ma silną nazwę, [ \<baza kodu > element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.</span><span class="sxs-lookup"><span data-stu-id="90c7a-106">If the assembly has a strong name, the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="90c7a-107">Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="90c7a-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="90c7a-108">Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="90c7a-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="90c7a-109">Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="90c7a-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c7a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90c7a-110">See also</span></span>

- [<span data-ttu-id="90c7a-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="90c7a-111">How the Runtime Locates Assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="90c7a-112">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="90c7a-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="90c7a-113">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="90c7a-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="90c7a-114">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="90c7a-114">Assemblies in .NET</span></span>](index.md)
