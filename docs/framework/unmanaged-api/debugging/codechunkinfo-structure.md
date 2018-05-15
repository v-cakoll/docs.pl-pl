---
title: CodeChunkInfo Structure1
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
ms.openlocfilehash: 6e3d138700ef06da7b40a88a768a41f3ffcb38eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="6c6b7-102">CodeChunkInfo Structure1</span><span class="sxs-lookup"><span data-stu-id="6c6b7-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="6c6b7-103">Reprezentuje pojedynczy fragmentu kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c6b7-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c6b7-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="6c6b7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6c6b7-105">Members</span></span>  
  
|<span data-ttu-id="6c6b7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6c6b7-106">Member</span></span>|<span data-ttu-id="6c6b7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6c6b7-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="6c6b7-108">A `CORDB_ADDRESS` wartość, która określa początkowy adres fragmentu.</span><span class="sxs-lookup"><span data-stu-id="6c6b7-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="6c6b7-109">Rozmiar w bajtach fragmentu.</span><span class="sxs-lookup"><span data-stu-id="6c6b7-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c6b7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c6b7-110">Remarks</span></span>  
 <span data-ttu-id="6c6b7-111">Jednego fragmentu kodu to region z kodu macierzystego, który jest częścią obiektu kodu, takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="6c6b7-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c6b7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c6b7-112">Requirements</span></span>  
 <span data-ttu-id="6c6b7-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6b7-114">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6c6b7-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="6c6b7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c6b7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c6b7-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6b7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c6b7-117">See Also</span></span>  
 [<span data-ttu-id="6c6b7-118">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="6c6b7-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="6c6b7-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6c6b7-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="6c6b7-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6c6b7-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
