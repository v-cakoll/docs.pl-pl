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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178289"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="fb2d0-102">AssemblyComparisonResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fb2d0-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="fb2d0-103">Wskazuje równoważność dwóch tożsamości zestawu, zgodnie z funkcją [CompareAssemblyIdentity.](compareassemblyidentity-function.md)</span><span class="sxs-lookup"><span data-stu-id="fb2d0-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb2d0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fb2d0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fb2d0-105">Members</span></span>  
  
|<span data-ttu-id="fb2d0-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="fb2d0-106">Member name</span></span>|<span data-ttu-id="fb2d0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fb2d0-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="fb2d0-108">Wskazuje, że wszystkie pola zestawu w meczu porównania.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="fb2d0-109">Wskazuje, że zestawy są uważane za równoważne na podstawie ujednolicenia wersji zestawu (CLR) common language runtime (Common Language Runtime Version) w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="fb2d0-110">Wskazuje częściowe dopasowanie zestawów na podstawie ujednolicenia CLR numerów wersji zestawu w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="fb2d0-111">Wskazuje częściowe dopasowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="fb2d0-112">Wskazuje częściowe dopasowanie zestawów na podstawie starszego ujednolicenia numerów wersji.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="fb2d0-113">Wskazuje częściowe dopasowanie po prostu nazwanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="fb2d0-114">Wskazuje, że zestawy są uważane za równoważne na podstawie ujednolicenia CLR numerów wersji w starszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="fb2d0-115">Wskazuje dopasowanie między dwoma po prostu nazwanych zestawów, których numery wersji zostały zignorowane.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="fb2d0-116">Wskazuje, że między dwoma zestawami nie doszło do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="fb2d0-117">Wskazuje, że dwa zestawy są zgodne z wyjątkiem ich numerów wersji, które pasują tylko częściowo.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="fb2d0-118">Wskazuje, że dwa zestawy są zgodne z wyjątkiem ich numerów wersji, które nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="fb2d0-119">Wskazuje, że przyczyna braku równoważności nie jest znana.</span><span class="sxs-lookup"><span data-stu-id="fb2d0-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb2d0-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb2d0-120">Requirements</span></span>  
 <span data-ttu-id="fb2d0-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb2d0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb2d0-122">**Nagłówek:** Fuzja.h</span><span class="sxs-lookup"><span data-stu-id="fb2d0-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fb2d0-123">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb2d0-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb2d0-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb2d0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2d0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb2d0-125">See also</span></span>

- [<span data-ttu-id="fb2d0-126">CompareAssemblyIdentity — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fb2d0-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="fb2d0-127">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="fb2d0-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
