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
ms.openlocfilehash: ee808ba403a513b897134420b45ebe8cd3537571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442249"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="14b48-102">CorLocalRefPreservation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="14b48-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="14b48-103">Zawiera wartości flagi dla przetwarzania lokalnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="14b48-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14b48-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="14b48-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="14b48-105">Members</span></span>  
  
|<span data-ttu-id="14b48-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="14b48-106">Member</span></span>|<span data-ttu-id="14b48-107">Opis</span><span class="sxs-lookup"><span data-stu-id="14b48-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="14b48-108">Zachowaj żadnych odwołań lokalnego.</span><span class="sxs-lookup"><span data-stu-id="14b48-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="14b48-109">Zachowaj odwołania do typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="14b48-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="14b48-110">Zachowaj odwołania do elementu członkowskiego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="14b48-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14b48-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14b48-111">Requirements</span></span>  
 <span data-ttu-id="14b48-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14b48-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14b48-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="14b48-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="14b48-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14b48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b48-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14b48-115">See Also</span></span>  
 [<span data-ttu-id="14b48-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="14b48-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
