---
title: CorManifestResourceFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: 35966e25d02bd6f1a9bdd21ad4e9cc44b7bb480e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450260"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="8fb1a-102">CorManifestResourceFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8fb1a-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="8fb1a-103">Wskazuje widoczność zasobów zakodowanych w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fb1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fb1a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8fb1a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8fb1a-105">Members</span></span>  
  
|<span data-ttu-id="8fb1a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8fb1a-106">Member</span></span>|<span data-ttu-id="8fb1a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8fb1a-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="8fb1a-108">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="8fb1a-109">Zasoby są publiczne.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="8fb1a-110">Zasoby są prywatne.</span><span class="sxs-lookup"><span data-stu-id="8fb1a-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8fb1a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fb1a-111">Requirements</span></span>  
 <span data-ttu-id="8fb1a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb1a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb1a-113">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8fb1a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8fb1a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb1a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb1a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fb1a-115">See also</span></span>

- [<span data-ttu-id="8fb1a-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8fb1a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
