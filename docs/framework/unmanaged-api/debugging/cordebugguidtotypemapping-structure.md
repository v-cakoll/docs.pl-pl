---
title: CorDebugGuidToTypeMapping — Struktura
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: 313f6649448653ad630d616c7dbf739653e352dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132841"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="4c36a-102">CorDebugGuidToTypeMapping — Struktura</span><span class="sxs-lookup"><span data-stu-id="4c36a-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="4c36a-103">Mapuje identyfikator GUID środowisko wykonawcze systemu Windows na odpowiedni obiekt ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="4c36a-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c36a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c36a-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="4c36a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4c36a-105">Members</span></span>  
  
|<span data-ttu-id="4c36a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4c36a-106">Member</span></span>|<span data-ttu-id="4c36a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4c36a-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="4c36a-108">Identyfikator GUID typu środowisko wykonawcze systemu Windows w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4c36a-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="4c36a-109">Wskaźnik do obiektu ICorDebugType, który zawiera informacje o typie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4c36a-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c36a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c36a-110">Requirements</span></span>  
 <span data-ttu-id="4c36a-111">**Platformy:** środowisko wykonawcze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4c36a-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="4c36a-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c36a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c36a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4c36a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c36a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c36a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c36a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c36a-115">See also</span></span>

- [<span data-ttu-id="4c36a-116">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="4c36a-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4c36a-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4c36a-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
