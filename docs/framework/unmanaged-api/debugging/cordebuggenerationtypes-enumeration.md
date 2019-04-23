---
title: CorDebugGenerationTypes — Wyliczenie
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1707a09f14fbab6150c2ecbcd188d7bf88064fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085899"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="33f69-102">CorDebugGenerationTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="33f69-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="33f69-103">Określa Generowanie region pamięci na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="33f69-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33f69-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="33f69-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="33f69-105">Members</span></span>  
  
|<span data-ttu-id="33f69-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="33f69-106">Member name</span></span>|<span data-ttu-id="33f69-107">Opis</span><span class="sxs-lookup"><span data-stu-id="33f69-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="33f69-108">Generacji 0.</span><span class="sxs-lookup"><span data-stu-id="33f69-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="33f69-109">Generacja 1.</span><span class="sxs-lookup"><span data-stu-id="33f69-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="33f69-110">2. generacji.</span><span class="sxs-lookup"><span data-stu-id="33f69-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="33f69-111">Stos dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="33f69-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33f69-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33f69-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f69-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33f69-113">Requirements</span></span>  
 <span data-ttu-id="33f69-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f69-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f69-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33f69-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33f69-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33f69-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33f69-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f69-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f69-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f69-118">See also</span></span>

- [<span data-ttu-id="33f69-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="33f69-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
