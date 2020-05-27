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
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009161"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="c811c-102">CorSetENC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c811c-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="c811c-103">Zawiera wartości używane do wpływania na zachowanie podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="c811c-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c811c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c811c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="c811c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c811c-105">Members</span></span>  
  
|<span data-ttu-id="c811c-106">Członek</span><span class="sxs-lookup"><span data-stu-id="c811c-106">Member</span></span>|<span data-ttu-id="c811c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c811c-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="c811c-108">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="c811c-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="c811c-109">Nieaktualne.</span><span class="sxs-lookup"><span data-stu-id="c811c-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="c811c-110">Wskazuje, że metadane można zaktualizować, nie można przenieść tokenów.</span><span class="sxs-lookup"><span data-stu-id="c811c-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="c811c-111">Wskazuje, że tokeny mogą być przenoszone podczas aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="c811c-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="c811c-112">Wskazuje, że aktualizacje mogą obejmować tylko dodatki.</span><span class="sxs-lookup"><span data-stu-id="c811c-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="c811c-113">Nie można przenieść tokenów.</span><span class="sxs-lookup"><span data-stu-id="c811c-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="c811c-114">Wskazuje, że kompilacja jest przyrostowa.</span><span class="sxs-lookup"><span data-stu-id="c811c-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="c811c-115">Wskazuje, że powinny być zapisane tylko zmienione metadane.</span><span class="sxs-lookup"><span data-stu-id="c811c-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="c811c-116">Obejmuje `MDUpdateENC` `MDUpdateFull` i `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="c811c-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c811c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c811c-117">Requirements</span></span>  
 <span data-ttu-id="c811c-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c811c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c811c-119">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c811c-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c811c-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c811c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c811c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c811c-121">See also</span></span>

- [<span data-ttu-id="c811c-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="c811c-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
