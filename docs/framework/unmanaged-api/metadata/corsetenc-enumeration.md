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
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="cb6cd-102">CorSetENC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cb6cd-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="cb6cd-103">Zawiera wartości używane do wpływają na zachowanie podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb6cd-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cb6cd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cb6cd-105">Members</span></span>  
  
|<span data-ttu-id="cb6cd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cb6cd-106">Member</span></span>|<span data-ttu-id="cb6cd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cb6cd-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="cb6cd-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="cb6cd-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="cb6cd-110">Wskazuje, że metadane mogą zostać uaktualnione, tokenów nie może zostać przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="cb6cd-111">Wskazuje, że tokeny mogą być przenoszone podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="cb6cd-112">Wskazuje, że aktualizacje może składać się tylko z dodatków.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="cb6cd-113">Nie można przenieść tokenów.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="cb6cd-114">Wskazuje, czy kompilacja jest przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="cb6cd-115">Wskazuje, że ma zostać zapisany tylko metadane zmienione.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="cb6cd-116">Obejmuje `MDUpdateENC`, `MDUpdateFull` i `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="cb6cd-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb6cd-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb6cd-117">Requirements</span></span>  
 <span data-ttu-id="cb6cd-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6cd-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cb6cd-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cb6cd-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6cd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6cd-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb6cd-121">See Also</span></span>  
 [<span data-ttu-id="cb6cd-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="cb6cd-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
