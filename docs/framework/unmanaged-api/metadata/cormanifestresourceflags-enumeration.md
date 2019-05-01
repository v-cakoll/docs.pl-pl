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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204f04b1ed1ea293639e0b9826f7e0ce6f384763
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992696"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="e2b44-102">CorManifestResourceFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e2b44-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="e2b44-103">Określa widoczność zasobów zakodowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="e2b44-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2b44-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e2b44-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e2b44-105">Members</span></span>  
  
|<span data-ttu-id="e2b44-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e2b44-106">Member</span></span>|<span data-ttu-id="e2b44-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e2b44-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="e2b44-108">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="e2b44-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="e2b44-109">Zasoby są publiczne.</span><span class="sxs-lookup"><span data-stu-id="e2b44-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="e2b44-110">Zasoby są prywatne.</span><span class="sxs-lookup"><span data-stu-id="e2b44-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2b44-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2b44-111">Requirements</span></span>  
 <span data-ttu-id="e2b44-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2b44-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2b44-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e2b44-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e2b44-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b44-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2b44-115">See also</span></span>

- [<span data-ttu-id="e2b44-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="e2b44-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
