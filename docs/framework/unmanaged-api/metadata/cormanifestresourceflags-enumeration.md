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
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440713"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="d400b-102">CorManifestResourceFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d400b-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="d400b-103">Określa widoczność zasobów zakodowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="d400b-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d400b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d400b-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d400b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d400b-105">Members</span></span>  
  
|<span data-ttu-id="d400b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d400b-106">Member</span></span>|<span data-ttu-id="d400b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d400b-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="d400b-108">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="d400b-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="d400b-109">Zasoby są publiczne.</span><span class="sxs-lookup"><span data-stu-id="d400b-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="d400b-110">Zasoby są prywatne.</span><span class="sxs-lookup"><span data-stu-id="d400b-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d400b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d400b-111">Requirements</span></span>  
 <span data-ttu-id="d400b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d400b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d400b-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d400b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d400b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d400b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d400b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d400b-115">See Also</span></span>  
 [<span data-ttu-id="d400b-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d400b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
