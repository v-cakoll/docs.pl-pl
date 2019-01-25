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
ms.openlocfilehash: a3d3ef78da9dd639d0f9050a8b61d1e365cd8b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650252"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="6ebbb-102">CorManifestResourceFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6ebbb-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="6ebbb-103">Określa widoczność zasobów zakodowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="6ebbb-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ebbb-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6ebbb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6ebbb-105">Members</span></span>  
  
|<span data-ttu-id="6ebbb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6ebbb-106">Member</span></span>|<span data-ttu-id="6ebbb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ebbb-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="6ebbb-108">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="6ebbb-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="6ebbb-109">Zasoby są publiczne.</span><span class="sxs-lookup"><span data-stu-id="6ebbb-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="6ebbb-110">Zasoby są prywatne.</span><span class="sxs-lookup"><span data-stu-id="6ebbb-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ebbb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ebbb-111">Requirements</span></span>  
 <span data-ttu-id="6ebbb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebbb-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6ebbb-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6ebbb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ebbb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebbb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ebbb-115">See also</span></span>
- [<span data-ttu-id="6ebbb-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="6ebbb-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
