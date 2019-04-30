---
title: Łączenie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697722"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="e9dc6-102">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="e9dc6-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="e9dc6-103">W tej sekcji opisano niezarządzane statyczne funkcje globalne, używane do łączenia interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9dc6-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e9dc6-104">In This Section</span></span>  
 [<span data-ttu-id="e9dc6-105">ClearDownloadCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-105">ClearDownloadCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 <span data-ttu-id="e9dc6-106">Czyści globalnej pamięci podręcznej zestawów pobrany.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="e9dc6-107">CompareAssemblyIdentity, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-107">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 <span data-ttu-id="e9dc6-108">Porównuje dwa tożsamości zestawu do ustalenia, czy są równoważne.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="e9dc6-109">CreateApplicationContext, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-109">CreateApplicationContext Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 <span data-ttu-id="e9dc6-110">Tylko do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-110">Internal only.</span></span> <span data-ttu-id="e9dc6-111">(Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="e9dc6-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="e9dc6-112">CreateAssemblyCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-112">CreateAssemblyCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 <span data-ttu-id="e9dc6-113">Pobiera wskaźnik do nowego [iassemblycache —](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) wystąpienia, która reprezentuje globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-113">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="e9dc6-114">CreateAssemblyEnum, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-114">CreateAssemblyEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 <span data-ttu-id="e9dc6-115">Pobiera wskaźnik do [iassemblyenum —](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienia, która reprezentuje listę obiektów, które istnieją w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-115">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="e9dc6-116">CreateAssemblyNameObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-116">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 <span data-ttu-id="e9dc6-117">Pobiera wskaźnik do [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, która reprezentuje unikatową tożsamość zestawu z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-117">Gets a pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="e9dc6-118">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-118">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 <span data-ttu-id="e9dc6-119">Tworzy czytnik historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="e9dc6-120">CreateInstallReferenceEnum, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-120">CreateInstallReferenceEnum Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 <span data-ttu-id="e9dc6-121">Pobiera wskaźnik do [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) wystąpienia, która reprezentuje listę aplikacji odwołania do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-121">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="e9dc6-122">GetAppIdAuthority, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-122">GetAppIdAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 <span data-ttu-id="e9dc6-123">Pobiera wskaźnik do [iappidauthority —](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienie, które zarządza kluczami, dokumentacji i tożsamości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-123">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="e9dc6-124">GetAssemblyIdentityFromFile, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-124">GetAssemblyIdentityFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="e9dc6-125">Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="e9dc6-126">GetCachePath, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-126">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 <span data-ttu-id="e9dc6-127">Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="e9dc6-128">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-128">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 <span data-ttu-id="e9dc6-129">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="e9dc6-130">GetIdentityAuthority, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-130">GetIdentityAuthority Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 <span data-ttu-id="e9dc6-131">Pobiera wskaźnik do [iidentityauthority —](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) wystąpienie, które zarządza kluczami obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-131">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="e9dc6-132">IsFrameworkAssembly, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-132">IsFrameworkAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 <span data-ttu-id="e9dc6-133">Pobiera wartość wskazującą, czy określony zestaw jest zarządzany.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="e9dc6-134">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-134">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 <span data-ttu-id="e9dc6-135">Usuwa wspólnego języka środowiska uruchomieniowego pamięci podręcznej pobierania.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="e9dc6-136">PreBindAssemblyEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="e9dc6-136">PreBindAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 <span data-ttu-id="e9dc6-137">Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="e9dc6-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9dc6-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e9dc6-138">Related Sections</span></span>  
 [<span data-ttu-id="e9dc6-139">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="e9dc6-139">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="e9dc6-140">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="e9dc6-140">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="e9dc6-141">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="e9dc6-141">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [<span data-ttu-id="e9dc6-142">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e9dc6-142">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
