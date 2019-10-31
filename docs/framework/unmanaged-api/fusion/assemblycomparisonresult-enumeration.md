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
ms.openlocfilehash: 3d3fd88a2c1ac90f823b23d8d2bcb5b177a625c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109010"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="fd12c-102">AssemblyComparisonResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fd12c-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="fd12c-103">Określa równoważność dwóch tożsamości zestawów określonych przez funkcję [CompareAssemblyIdentity —](compareassemblyidentity-function.md) .</span><span class="sxs-lookup"><span data-stu-id="fd12c-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd12c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd12c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="fd12c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fd12c-105">Members</span></span>  
  
|<span data-ttu-id="fd12c-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fd12c-106">Member name</span></span>|<span data-ttu-id="fd12c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fd12c-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="fd12c-108">Wskazuje, że wszystkie pola zestawu w porównaniu są zgodne.</span><span class="sxs-lookup"><span data-stu-id="fd12c-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="fd12c-109">Wskazuje, że zestawy są uważane za równoważne w oparciu o wersję środowiska uruchomieniowego języka wspólnego (CLR), w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="fd12c-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="fd12c-110">Wskazuje częściowe dopasowanie zestawów na podstawie niezjednoczenia środowiska CLR numerów wersji zestawu w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="fd12c-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="fd12c-111">Wskazuje częściowe dopasowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="fd12c-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="fd12c-112">Wskazuje częściowe dopasowanie zestawów w oparciu o starszej zjednoczenia numerów wersji.</span><span class="sxs-lookup"><span data-stu-id="fd12c-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="fd12c-113">Wskazuje częściowe dopasowanie zestawów po prostu nazwanych.</span><span class="sxs-lookup"><span data-stu-id="fd12c-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="fd12c-114">Wskazuje, że zestawy są uważane za równoważne w oparciu o niezjednoczenie kodów wersji w starszych wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd12c-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="fd12c-115">Wskazuje zgodność między dwoma po prostu zestawami, których numery wersji zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="fd12c-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="fd12c-116">Wskazuje, że nie wystąpiły żadne dopasowanie między dwoma zestawami.</span><span class="sxs-lookup"><span data-stu-id="fd12c-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="fd12c-117">Wskazuje, że dwa zestawy są zgodne z wyjątkiem numerów wersji, które pasują tylko częściowo.</span><span class="sxs-lookup"><span data-stu-id="fd12c-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="fd12c-118">Wskazuje, że dwa zestawy są zgodne z wyjątkiem numerów wersji, które nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="fd12c-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="fd12c-119">Wskazuje, że przyczyna nierównoważności jest nieznana.</span><span class="sxs-lookup"><span data-stu-id="fd12c-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd12c-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd12c-120">Requirements</span></span>  
 <span data-ttu-id="fd12c-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd12c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd12c-122">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fd12c-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fd12c-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fd12c-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd12c-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd12c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd12c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd12c-125">See also</span></span>

- [<span data-ttu-id="fd12c-126">CompareAssemblyIdentity, funkcja</span><span class="sxs-lookup"><span data-stu-id="fd12c-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="fd12c-127">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="fd12c-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
