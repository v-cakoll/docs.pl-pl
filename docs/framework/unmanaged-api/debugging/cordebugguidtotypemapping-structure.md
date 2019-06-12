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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025997"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="15721-102">CorDebugGuidToTypeMapping — Struktura</span><span class="sxs-lookup"><span data-stu-id="15721-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="15721-103">Mapuje jego odpowiedni obiekt ICorDebugType GUID środowiska wykonawczego Windows.</span><span class="sxs-lookup"><span data-stu-id="15721-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15721-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15721-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="15721-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="15721-105">Members</span></span>  
  
|<span data-ttu-id="15721-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="15721-106">Member</span></span>|<span data-ttu-id="15721-107">Opis</span><span class="sxs-lookup"><span data-stu-id="15721-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="15721-108">Identyfikator GUID typu pamięci podręcznej środowiska wykonawczego Windows.</span><span class="sxs-lookup"><span data-stu-id="15721-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="15721-109">Wskaźnik do obiektu ICorDebugType, który zawiera informacje o typie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="15721-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15721-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15721-110">Requirements</span></span>  
 <span data-ttu-id="15721-111">**Platformy:** Środowisko uruchomieniowe Windows.</span><span class="sxs-lookup"><span data-stu-id="15721-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="15721-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15721-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15721-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15721-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15721-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15721-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15721-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15721-115">See also</span></span>

- [<span data-ttu-id="15721-116">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="15721-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="15721-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="15721-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
