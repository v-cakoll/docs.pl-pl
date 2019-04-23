---
title: CorLocalRefPreservation — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 845994b96445d8ec2a0e37affc5164b432894a91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102196"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="465d8-102">CorLocalRefPreservation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="465d8-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="465d8-103">Zawiera wartości flagi dla przetwarzania lokalnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="465d8-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="465d8-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="465d8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="465d8-105">Members</span></span>  
  
|<span data-ttu-id="465d8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="465d8-106">Member</span></span>|<span data-ttu-id="465d8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="465d8-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="465d8-108">Zachowaj żadnych odwołań lokalnych.</span><span class="sxs-lookup"><span data-stu-id="465d8-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="465d8-109">Zachowaj lokalne typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="465d8-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="465d8-110">Zachowane odwołania do elementu członkowskiego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="465d8-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="465d8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="465d8-111">Requirements</span></span>  
 <span data-ttu-id="465d8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="465d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="465d8-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="465d8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="465d8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="465d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465d8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="465d8-115">See also</span></span>

- [<span data-ttu-id="465d8-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="465d8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
