---
title: CodeChunkInfo, struktura
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2baefa45deb8c13e8c1e627724fbe271b210a9ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740883"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="c2a5c-102">CodeChunkInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="c2a5c-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="c2a5c-103">Reprezentuje jeden fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2a5c-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="c2a5c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c2a5c-105">Members</span></span>  
  
|<span data-ttu-id="c2a5c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c2a5c-106">Member</span></span>|<span data-ttu-id="c2a5c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c2a5c-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="c2a5c-108">A `CORDB_ADDRESS` wartość, która określa adres początkowy fragmentów.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="c2a5c-109">Rozmiar w bajtach fragmentów.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2a5c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2a5c-110">Remarks</span></span>  
 <span data-ttu-id="c2a5c-111">Jeden fragment kodu jest obszarem kodu macierzystego, który jest częścią obiektu kodu, takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="c2a5c-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a5c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2a5c-112">Requirements</span></span>  
 <span data-ttu-id="c2a5c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a5c-114">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c2a5c-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c2a5c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a5c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2a5c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a5c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2a5c-117">See also</span></span>

- [<span data-ttu-id="c2a5c-118">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="c2a5c-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="c2a5c-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="c2a5c-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c2a5c-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c2a5c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
