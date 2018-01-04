---
title: Umieszczanie zestawu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6669783cf6cac94e8b2335d4b475f1e2b6c5e7e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-placement"></a><span data-ttu-id="29604-102">Umieszczanie zestawu</span><span class="sxs-lookup"><span data-stu-id="29604-102">Assembly Placement</span></span>
<span data-ttu-id="29604-103">Dla większości aplikacji .NET Framework można zlokalizować zestawów, które tworzą aplikację w katalogu aplikacji, w podkatalogu w katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniana).</span><span class="sxs-lookup"><span data-stu-id="29604-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="29604-104">Można zastąpić, gdy środowisko uruchomieniowe języka wspólnego szuka zestawu, za pomocą [ \<codeBase > elementu](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="29604-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="29604-105">Jeśli zestaw nie ma silnej nazwy, lokalizacji określonej za pomocą [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) jest ograniczona do katalogu aplikacji lub podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="29604-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="29604-106">Jeśli zestaw ma silną nazwę [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) mogą określić dowolną lokalizację, na komputerze lub w sieci.</span><span class="sxs-lookup"><span data-stu-id="29604-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="29604-107">Podobne reguły mają zastosowanie do lokalizowania zestawów podczas pracy z kodem niezarządzanym lub aplikacje międzyoperacyjne COM: Jeśli zestaw zostaną udostępnione przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="29604-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="29604-108">Zestawy używane z kodem niezarządzanym musi być eksportowane jako biblioteki typów i zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="29604-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="29604-109">Zestawy używane przez współdziałanie z COM musi być zarejestrowany w wykazie, chociaż w niektórych przypadkach rejestracja odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="29604-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29604-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29604-110">See Also</span></span>  
 [<span data-ttu-id="29604-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="29604-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="29604-112">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="29604-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="29604-113">Współdziałanie COM zaawansowane</span><span class="sxs-lookup"><span data-stu-id="29604-113">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="29604-114">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="29604-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
