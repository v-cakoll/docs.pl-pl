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
ms.openlocfilehash: ebdff88e9fdf499b809d56c4c29a906dbef9ec40
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008979"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="8f995-102">CorManifestResourceFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8f995-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="8f995-103">Wskazuje widoczność zasobów zakodowanych w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="8f995-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f995-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f995-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8f995-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8f995-105">Members</span></span>  
  
|<span data-ttu-id="8f995-106">Członek</span><span class="sxs-lookup"><span data-stu-id="8f995-106">Member</span></span>|<span data-ttu-id="8f995-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8f995-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="8f995-108">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="8f995-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="8f995-109">Zasoby są publiczne.</span><span class="sxs-lookup"><span data-stu-id="8f995-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="8f995-110">Zasoby są prywatne.</span><span class="sxs-lookup"><span data-stu-id="8f995-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f995-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f995-111">Requirements</span></span>  
 <span data-ttu-id="8f995-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f995-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f995-113">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8f995-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8f995-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f995-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f995-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f995-115">See also</span></span>

- [<span data-ttu-id="8f995-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8f995-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
