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
ms.openlocfilehash: 5fb663bc17458f0866e66332e40527390714fc79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720451"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="3bdc1-102">CorDebugGenerationTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3bdc1-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="3bdc1-103">Określa Generowanie region pamięci na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3bdc1-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdc1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bdc1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="3bdc1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3bdc1-105">Members</span></span>  
  
|<span data-ttu-id="3bdc1-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3bdc1-106">Member name</span></span>|<span data-ttu-id="3bdc1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3bdc1-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="3bdc1-108">Generacji 0.</span><span class="sxs-lookup"><span data-stu-id="3bdc1-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="3bdc1-109">Generacja 1.</span><span class="sxs-lookup"><span data-stu-id="3bdc1-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="3bdc1-110">2. generacji.</span><span class="sxs-lookup"><span data-stu-id="3bdc1-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="3bdc1-111">Stos dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="3bdc1-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bdc1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bdc1-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdc1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bdc1-113">Requirements</span></span>  
 <span data-ttu-id="3bdc1-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bdc1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bdc1-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bdc1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bdc1-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bdc1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bdc1-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bdc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdc1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3bdc1-118">See also</span></span>
- [<span data-ttu-id="3bdc1-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3bdc1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
