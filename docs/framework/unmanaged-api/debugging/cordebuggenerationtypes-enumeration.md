---
title: "CorDebugGenerationTypes — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9b5126958b17ee2d1de5394ed07d78c3ffe29b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="52613-102">CorDebugGenerationTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="52613-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="52613-103">Określa Generowanie obszaru pamięci na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="52613-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52613-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52613-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="52613-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="52613-105">Members</span></span>  
  
|<span data-ttu-id="52613-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="52613-106">Member name</span></span>|<span data-ttu-id="52613-107">Opis</span><span class="sxs-lookup"><span data-stu-id="52613-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="52613-108">Generacji 0.</span><span class="sxs-lookup"><span data-stu-id="52613-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="52613-109">Generacja 1.</span><span class="sxs-lookup"><span data-stu-id="52613-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="52613-110">Generacji 2.</span><span class="sxs-lookup"><span data-stu-id="52613-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="52613-111">Sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="52613-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52613-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52613-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52613-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52613-113">Requirements</span></span>  
 <span data-ttu-id="52613-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52613-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52613-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52613-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52613-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52613-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52613-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52613-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52613-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52613-118">See Also</span></span>  
 [<span data-ttu-id="52613-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="52613-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
