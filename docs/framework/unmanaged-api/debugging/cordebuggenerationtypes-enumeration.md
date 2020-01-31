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
ms.openlocfilehash: 6133b34a60fd06c1b75d69783760741b8de62071
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789341"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="62681-102">CorDebugGenerationTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="62681-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="62681-103">Określa generowanie regionu pamięci na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="62681-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62681-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62681-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="62681-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="62681-105">Members</span></span>  
  
|<span data-ttu-id="62681-106">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="62681-106">Member name</span></span>|<span data-ttu-id="62681-107">Opis</span><span class="sxs-lookup"><span data-stu-id="62681-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="62681-108">Generacja 0.</span><span class="sxs-lookup"><span data-stu-id="62681-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="62681-109">Generacja 1.</span><span class="sxs-lookup"><span data-stu-id="62681-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="62681-110">Generacja 2.</span><span class="sxs-lookup"><span data-stu-id="62681-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="62681-111">Sterta dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="62681-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62681-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62681-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62681-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62681-113">Requirements</span></span>  
 <span data-ttu-id="62681-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62681-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62681-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62681-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62681-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="62681-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62681-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62681-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62681-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62681-118">See also</span></span>

- [<span data-ttu-id="62681-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="62681-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
