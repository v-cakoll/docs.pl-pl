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
ms.openlocfilehash: 58c9d4c66af0bb9f4e66d17b18ac78ef8271bc31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072665"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="bfcfd-102">CodeChunkInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="bfcfd-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="bfcfd-103">Reprezentuje jeden fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bfcfd-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcfd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfcfd-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="bfcfd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bfcfd-105">Members</span></span>  
  
|<span data-ttu-id="bfcfd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bfcfd-106">Member</span></span>|<span data-ttu-id="bfcfd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bfcfd-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="bfcfd-108">A `CORDB_ADDRESS` wartość, która określa adres początkowy fragmentów.</span><span class="sxs-lookup"><span data-stu-id="bfcfd-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="bfcfd-109">Rozmiar w bajtach fragmentów.</span><span class="sxs-lookup"><span data-stu-id="bfcfd-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfcfd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfcfd-110">Remarks</span></span>  
 <span data-ttu-id="bfcfd-111">Jeden fragment kodu jest obszarem kodu macierzystego, który jest częścią obiektu kodu, takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="bfcfd-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcfd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfcfd-112">Requirements</span></span>  
 <span data-ttu-id="bfcfd-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfcfd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcfd-114">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="bfcfd-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="bfcfd-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfcfd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfcfd-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcfd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcfd-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfcfd-117">See also</span></span>

- [<span data-ttu-id="bfcfd-118">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="bfcfd-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="bfcfd-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="bfcfd-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="bfcfd-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bfcfd-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
