---
title: Interfejsy łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 81c66825e69d9526abddfe06133426a2274ad08f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108194"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="65c68-102">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="65c68-102">Fusion Interfaces</span></span>
<span data-ttu-id="65c68-103">W tej sekcji opisano niezarządzane interfejsy, które są używane przez interfejs API Fusion do uzyskiwania dostępu do właściwości zasobów aplikacji i lokalizowania odpowiednich wersji tych zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65c68-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65c68-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="65c68-104">In This Section</span></span>  
 [<span data-ttu-id="65c68-105">IAppIdAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="65c68-106">Dostarcza metody, które generują i porównują klucze dla tożsamości i odwołań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65c68-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="65c68-107">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="65c68-108">Przedstawia reprezentację globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="65c68-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="65c68-109">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="65c68-110">Reprezentuje pojedynczy zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="65c68-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="65c68-111">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="65c68-112">Reprezentuje moduł wyliczający dla tablicy `IAssemblyName` obiektów.</span><span class="sxs-lookup"><span data-stu-id="65c68-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="65c68-113">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="65c68-114">Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.</span><span class="sxs-lookup"><span data-stu-id="65c68-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="65c68-115">IDefinitionAppId, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="65c68-116">Reprezentuje unikatowy identyfikator kodu, który definiuje aplikację w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65c68-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="65c68-117">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="65c68-118">Reprezentuje unikatowy podpis kodu, który definiuje aplikację w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65c68-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="65c68-119">IEnumDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="65c68-120">Służy jako moduł wyliczający dla kolekcji obiektów `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="65c68-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="65c68-121">IEnumIDENTITY_ATTRIBUTE, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="65c68-122">Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65c68-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="65c68-123">IEnumReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="65c68-124">Służy jako moduł wyliczający dla kolekcji obiektów `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="65c68-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="65c68-125">IIdentityAuthority, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="65c68-126">Zarządza kluczami tożsamości dla obiektów kodu.</span><span class="sxs-lookup"><span data-stu-id="65c68-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="65c68-127">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="65c68-128">Reprezentuje moduł wyliczający dla zestawów, do których istnieją odwołania zainstalowane w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="65c68-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="65c68-129">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="65c68-130">Reprezentuje element zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="65c68-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="65c68-131">IReferenceAppId, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="65c68-132">Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="65c68-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="65c68-133">IReferenceIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="65c68-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="65c68-134">Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="65c68-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="65c68-135">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="65c68-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="65c68-136">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="65c68-136">Related Sections</span></span>  
 [<span data-ttu-id="65c68-137">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="65c68-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="65c68-138">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="65c68-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="65c68-139">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="65c68-139">Fusion Structures</span></span>](fusion-structures.md)
