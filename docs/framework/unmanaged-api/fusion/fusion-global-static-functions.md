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
ms.openlocfilehash: 6a8f15bc862c0486311960f7567c49424859846e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795316"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="91262-102">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="91262-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="91262-103">W tej sekcji opisano niezarządzane globalne funkcje statyczne używane przez interfejs API Fusion.</span><span class="sxs-lookup"><span data-stu-id="91262-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91262-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="91262-104">In This Section</span></span>  
 [<span data-ttu-id="91262-105">ClearDownloadCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="91262-106">Czyści globalną pamięć podręczną zestawów pobranych zestawów.</span><span class="sxs-lookup"><span data-stu-id="91262-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="91262-107">CompareAssemblyIdentity, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="91262-108">Porównuje dwie tożsamości zestawów, aby określić, czy są one równoważne.</span><span class="sxs-lookup"><span data-stu-id="91262-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="91262-109">CreateApplicationContext, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="91262-110">Tylko wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="91262-110">Internal only.</span></span> <span data-ttu-id="91262-111">(Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).</span><span class="sxs-lookup"><span data-stu-id="91262-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="91262-112">CreateAssemblyCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="91262-113">Pobiera wskaźnik do nowego wystąpienia [IAssemblyCache](iassemblycache-interface.md) , które reprezentuje globalną pamięć podręczną zestawów.</span><span class="sxs-lookup"><span data-stu-id="91262-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="91262-114">CreateAssemblyEnum, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="91262-115">Pobiera wskaźnik do wystąpienia [IAssemblyEnum](iassemblyenum-interface.md) , które reprezentuje listę obiektów istniejących w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="91262-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="91262-116">CreateAssemblyNameObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="91262-117">Pobiera wskaźnik do wystąpienia [IAssemblyName](iassemblyname-interface.md) , które reprezentuje unikatową tożsamość zestawu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="91262-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="91262-118">CreateHistoryReader, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="91262-119">Tworzy czytelnika historii dla określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="91262-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="91262-120">CreateInstallReferenceEnum, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="91262-121">Pobiera wskaźnik do wystąpienia [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , które reprezentuje listę odwołań aplikacji do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="91262-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="91262-122">GetAppIdAuthority, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="91262-123">Pobiera wskaźnik do wystąpienia [IAppIdAuthority —](iappidauthority-interface.md) , które zarządza kluczami dla tożsamości i odwołań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91262-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="91262-124">GetAssemblyIdentityFromFile, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="91262-125">Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie w określonej ścieżce pliku.</span><span class="sxs-lookup"><span data-stu-id="91262-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="91262-126">GetCachePath, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="91262-127">Pobiera ścieżkę do buforowanego zestawu przy użyciu określonych flag.</span><span class="sxs-lookup"><span data-stu-id="91262-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="91262-128">GetHistoryFileDirectory, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="91262-129">Pobiera ścieżkę katalogu historii aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91262-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="91262-130">GetIdentityAuthority, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="91262-131">Pobiera wskaźnik do wystąpienia [IIdentityAuthority —](iidentityauthority-interface.md) , które zarządza kluczami obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="91262-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="91262-132">IsFrameworkAssembly, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="91262-133">Pobiera wartość wskazującą, czy określony zestaw jest zarządzany.</span><span class="sxs-lookup"><span data-stu-id="91262-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="91262-134">NukeDownloadedCache, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="91262-135">Usuwa pamięć podręczną pobierania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="91262-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="91262-136">PreBindAssemblyEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="91262-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="91262-137">Pobiera nazwę wyświetlaną dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="91262-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91262-138">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="91262-138">Related Sections</span></span>  
 [<span data-ttu-id="91262-139">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="91262-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="91262-140">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="91262-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="91262-141">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="91262-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="91262-142">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="91262-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
