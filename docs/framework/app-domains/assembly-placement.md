---
title: Umieszczanie zestawu
description: Przejrzyj wskazówki dotyczące umieszczania zestawów .NET w katalogach (na przykład w globalnej pamięci podręcznej zestawów lub w katalogu lub podkatalogu aplikacji).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104956"
---
# <a name="assembly-placement"></a><span data-ttu-id="14b07-103">Umieszczanie zestawu</span><span class="sxs-lookup"><span data-stu-id="14b07-103">Assembly Placement</span></span>
<span data-ttu-id="14b07-104">W przypadku większości aplikacji .NET Framework można zlokalizować zestawy, które tworzą aplikację w katalogu aplikacji, w podkatalogu katalogu aplikacji lub w globalnej pamięci podręcznej zestawów (Jeśli zestaw jest udostępniony).</span><span class="sxs-lookup"><span data-stu-id="14b07-104">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="14b07-105">Można przesłonić, gdzie środowisko uruchomieniowe języka wspólnego szuka zestawu przy użyciu [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="14b07-105">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="14b07-106">Jeśli zestaw nie ma silnej nazwy, lokalizacja określona za pomocą [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) jest ograniczona do katalogu aplikacji lub podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="14b07-106">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="14b07-107">Jeśli zestaw ma silną nazwę, [ \<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md) może określić dowolną lokalizację na komputerze lub w sieci.</span><span class="sxs-lookup"><span data-stu-id="14b07-107">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="14b07-108">Podobne reguły dotyczą lokalizowania zestawów podczas pracy z niezarządzanym kodem lub aplikacjami międzyoperacyjnymi modelu COM: Jeśli zestaw będzie współużytkowany przez wiele aplikacji, powinien być zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="14b07-108">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="14b07-109">Zestawy używane z kodem niezarządzanym muszą zostać wyeksportowane jako biblioteka typów i zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="14b07-109">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="14b07-110">Zestawy używane przez międzyoperacyjność modelu COM muszą być zarejestrowane w wykazie, chociaż w niektórych przypadkach ta rejestracja odbywa się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="14b07-110">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b07-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14b07-111">See also</span></span>

- [<span data-ttu-id="14b07-112">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="14b07-112">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="14b07-113">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="14b07-113">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="14b07-114">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="14b07-114">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="14b07-115">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="14b07-115">Assemblies in .NET</span></span>](index.md)
