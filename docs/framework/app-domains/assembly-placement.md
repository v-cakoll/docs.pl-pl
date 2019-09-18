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
ms.openlocfilehash: 6281a0f68fa0ce81b4763d8d0e8f17b47771d2ff
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053201"
---
# <a name="assembly-placement"></a><span data-ttu-id="6bbaa-102">Umieszczanie zestawu</span><span class="sxs-lookup"><span data-stu-id="6bbaa-102">Assembly Placement</span></span>
<span data-ttu-id="6bbaa-103">W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony).</span><span class="sxs-lookup"><span data-stu-id="6bbaa-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="6bbaa-104">Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<kodu bazowej >](../configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="6bbaa-105">Jeśli zestaw nie ma silnej nazwy, lokalizacja określona przy użyciu [ \<bazowej kodu > element](../configure-apps/file-schema/runtime/codebase-element.md) jest ograniczone do katalogu aplikacji lub podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="6bbaa-106">Jeśli zestaw ma silną nazwę, [ \<baza kodu > element](../configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-106">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="6bbaa-107">Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="6bbaa-108">Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="6bbaa-109">Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="6bbaa-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbaa-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bbaa-110">See also</span></span>

- [<span data-ttu-id="6bbaa-111">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6bbaa-111">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6bbaa-112">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6bbaa-112">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="6bbaa-113">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="6bbaa-113">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="6bbaa-114">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="6bbaa-114">Assemblies in .NET</span></span>](index.md)
