---
title: CorSetENC — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fd903cb4a9ce664b7a1c958a3fef0c639d6845d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122320"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="4979c-102">CorSetENC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4979c-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="4979c-103">Zawiera wartości używane do wywierania wpływu na zachowanie podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="4979c-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4979c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4979c-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="4979c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4979c-105">Members</span></span>  
  
|<span data-ttu-id="4979c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4979c-106">Member</span></span>|<span data-ttu-id="4979c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4979c-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="4979c-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="4979c-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="4979c-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="4979c-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="4979c-110">Wskazuje, że może zostać uaktualnione metadane, tokeny nie mogą być przenoszone.</span><span class="sxs-lookup"><span data-stu-id="4979c-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="4979c-111">Wskazuje, że tokeny mogą być przenoszone podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4979c-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="4979c-112">Wskazuje, że aktualizacje może składać się tylko z dodatków.</span><span class="sxs-lookup"><span data-stu-id="4979c-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="4979c-113">Nie można przenieść tokenów.</span><span class="sxs-lookup"><span data-stu-id="4979c-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="4979c-114">Wskazuje, że kompilacja jest przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="4979c-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="4979c-115">Wskazuje, że powinny być zapisywane tylko zmienione metadane.</span><span class="sxs-lookup"><span data-stu-id="4979c-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="4979c-116">Obejmuje `MDUpdateENC`, `MDUpdateFull` i `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="4979c-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4979c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4979c-117">Requirements</span></span>  
 <span data-ttu-id="4979c-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4979c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4979c-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4979c-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="4979c-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4979c-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4979c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4979c-121">See also</span></span>

- [<span data-ttu-id="4979c-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="4979c-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
