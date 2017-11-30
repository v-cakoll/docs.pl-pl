---
title: "CorLocalRefPreservation — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eac01ce31e850eb02af84c0b84e58c1f0142242d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="1007a-102">CorLocalRefPreservation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1007a-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="1007a-103">Zawiera wartości flagi dla przetwarzania lokalnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="1007a-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1007a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1007a-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="1007a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1007a-105">Members</span></span>  
  
|<span data-ttu-id="1007a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1007a-106">Member</span></span>|<span data-ttu-id="1007a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1007a-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="1007a-108">Zachowaj żadnych odwołań lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1007a-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="1007a-109">Zachowaj odwołania do typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1007a-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="1007a-110">Zachowaj odwołania do elementu członkowskiego lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1007a-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1007a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1007a-111">Requirements</span></span>  
 <span data-ttu-id="1007a-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1007a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1007a-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1007a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1007a-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1007a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1007a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1007a-115">See Also</span></span>  
 [<span data-ttu-id="1007a-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="1007a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
