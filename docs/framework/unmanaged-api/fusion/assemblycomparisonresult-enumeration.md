---
title: AssemblyComparisonResult — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141703"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="2224a-102">AssemblyComparisonResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2224a-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="2224a-103">Wskazuje na równoważność dwóch tożsamości zestawu, zgodnie z ustaleniami [compareassemblyidentity —](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="2224a-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2224a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2224a-104">Syntax</span></span>  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="2224a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2224a-105">Members</span></span>  
  
|<span data-ttu-id="2224a-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="2224a-106">Member name</span></span>|<span data-ttu-id="2224a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2224a-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="2224a-108">Wskazuje, że zestaw wszystkich pól dopasowania porównania.</span><span class="sxs-lookup"><span data-stu-id="2224a-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="2224a-109">Wskazuje, że zestawy są uważane za równoważne oparte na wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji ujednolicenie numery wersji zestawu w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="2224a-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="2224a-110">Wskazuje częściowe dopasowanie zestawów, w oparciu o ujednolicenie środowiska CLR numery wersji zestawu w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2224a-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="2224a-111">Wskazuje częściowe dopasowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="2224a-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="2224a-112">Wskazuje częściowym zestawy oparte na starszych ujednolicenie numerów wersji.</span><span class="sxs-lookup"><span data-stu-id="2224a-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="2224a-113">Wskazuje częściowe dopasowanie, po prostu nazwanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="2224a-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="2224a-114">Wskazuje, że zestawy są uważane za równoważne oparte na ujednolicenie środowiska CLR numery wersji w starszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2224a-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="2224a-115">Wskazuje zgodność między dwa po prostu nazwane zestawy, których numery wersji zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="2224a-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="2224a-116">Wskazuje, że dopasowanie nie wystąpił między dwoma zestawami.</span><span class="sxs-lookup"><span data-stu-id="2224a-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="2224a-117">Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji i tylko częściowo zgodne.</span><span class="sxs-lookup"><span data-stu-id="2224a-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="2224a-118">Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji, które nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="2224a-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="2224a-119">Wskazuje przyczynę niż równoważności jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="2224a-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2224a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2224a-120">Requirements</span></span>  
 <span data-ttu-id="2224a-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2224a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2224a-122">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2224a-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2224a-123">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2224a-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2224a-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2224a-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2224a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2224a-125">See also</span></span>

- [<span data-ttu-id="2224a-126">CompareAssemblyIdentity — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2224a-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [<span data-ttu-id="2224a-127">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="2224a-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
