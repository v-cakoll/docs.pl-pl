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
ms.openlocfilehash: ec072463c30e3463ba5a362ed389e7ab530ec1a7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781313"
---
# <a name="assembly-placement"></a><span data-ttu-id="3d672-102">Umieszczanie zestawu</span><span class="sxs-lookup"><span data-stu-id="3d672-102">Assembly Placement</span></span>
<span data-ttu-id="3d672-103">W przypadku większości aplikacji .NET Framework można umieścić zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej (Jeśli zestaw jest udostępniana).</span><span class="sxs-lookup"><span data-stu-id="3d672-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="3d672-104">Można zastąpić, których środowisko uruchomieniowe języka wspólnego szuka zestawu, za pomocą [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3d672-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="3d672-105">Jeśli zestaw nie ma silnej nazwy, lokalizacji określonej przy użyciu [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) jest ograniczony do katalogu aplikacji lub podkatalog.</span><span class="sxs-lookup"><span data-stu-id="3d672-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="3d672-106">Jeśli zestaw ma silną nazwą, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) mogą określić dowolną lokalizację, na komputerze lub w sieci.</span><span class="sxs-lookup"><span data-stu-id="3d672-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="3d672-107">Podobne zasady dotyczą lokalizowanie zestawów podczas pracy z kodem niezarządzanym lub aplikacje międzyoperacyjne COM: Jeśli zestaw zostanie udostępniony przez wiele aplikacji, należy zainstalować w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3d672-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="3d672-108">Zestawy używane z kodem niezarządzanym musi być wyeksportowany jako bibliotekę typów i zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="3d672-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="3d672-109">Zespoły korzystają z modelu COM musi być zarejestrowana w wykazie, chociaż w niektórych przypadkach rejestracja odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="3d672-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d672-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d672-110">See Also</span></span>  
 [<span data-ttu-id="3d672-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3d672-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="3d672-112">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d672-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="3d672-113">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="3d672-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="3d672-114">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="3d672-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
