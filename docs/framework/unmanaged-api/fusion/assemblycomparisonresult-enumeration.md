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
ms.openlocfilehash: 82b81ec29dece182548ead046edc7cb754fbf00e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="b0a52-102">AssemblyComparisonResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b0a52-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="b0a52-103">Wskazuje równoważność tożsamości dwóch zestawów, zgodnie z ustaleniami [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="b0a52-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0a52-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b0a52-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b0a52-105">Members</span></span>  
  
|<span data-ttu-id="b0a52-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b0a52-106">Member name</span></span>|<span data-ttu-id="b0a52-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b0a52-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="b0a52-108">Wskazuje, że zestaw wszystkich pól w dopasowania porównania.</span><span class="sxs-lookup"><span data-stu-id="b0a52-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="b0a52-109">Wskazuje, że zestawy zostały uznane za równorzędne oparte na wspólnej ujednolicenie środowiska uruchomieniowego języka wersji (języka wspólnego CLR) numerów wersji zestawu w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b0a52-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="b0a52-110">Wskazuje częściowe dopasowanie zestawów, w oparciu o ujednolicenie CLR numerów wersji zestawu w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b0a52-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="b0a52-111">Wskazuje częściowe dopasowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="b0a52-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="b0a52-112">Wskazuje częściowe dopasowanie zestawów, w oparciu o starszych ujednolicenie numerów wersji.</span><span class="sxs-lookup"><span data-stu-id="b0a52-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="b0a52-113">Wskazuje częściowe dopasowanie po prostu nazwane zestawy.</span><span class="sxs-lookup"><span data-stu-id="b0a52-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="b0a52-114">Wskazuje, że zestawy zostały uznane za równorzędne oparte na ujednolicenie CLR numerów wersji w starszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0a52-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="b0a52-115">Wskazuje zgodność między dwa po prostu nazwane zestawy, których numery wersji zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="b0a52-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="b0a52-116">Wskazuje, czy nie wystąpił między dwoma zestawami.</span><span class="sxs-lookup"><span data-stu-id="b0a52-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="b0a52-117">Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji tylko częściowo zgodne.</span><span class="sxs-lookup"><span data-stu-id="b0a52-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="b0a52-118">Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji, które nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="b0a52-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="b0a52-119">Wskazuje, przyczyna nie when jest nieznana.</span><span class="sxs-lookup"><span data-stu-id="b0a52-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0a52-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0a52-120">Requirements</span></span>  
 <span data-ttu-id="b0a52-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a52-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a52-122">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b0a52-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b0a52-123">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0a52-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0a52-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a52-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a52-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0a52-125">See Also</span></span>  
 [<span data-ttu-id="b0a52-126">CompareAssemblyIdentity, funkcja</span><span class="sxs-lookup"><span data-stu-id="b0a52-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [<span data-ttu-id="b0a52-127">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="b0a52-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
