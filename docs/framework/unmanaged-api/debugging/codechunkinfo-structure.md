---
title: CodeChunkInfo — Struktura
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
ms.openlocfilehash: 36afee8af3de046683c55215a677a529b0837c77
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274256"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="22854-102">CodeChunkInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="22854-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="22854-103">Reprezentuje pojedynczy fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="22854-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22854-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22854-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="22854-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22854-105">Members</span></span>  
  
|<span data-ttu-id="22854-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="22854-106">Member</span></span>|<span data-ttu-id="22854-107">Opis</span><span class="sxs-lookup"><span data-stu-id="22854-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="22854-108">`CORDB_ADDRESS` Wartość określająca początkowy adres fragmentu.</span><span class="sxs-lookup"><span data-stu-id="22854-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="22854-109">Rozmiar fragmentu, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="22854-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22854-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22854-110">Remarks</span></span>  
 <span data-ttu-id="22854-111">Pojedynczy fragment kodu jest regionem kodu natywnego, który jest częścią obiektu kodu, takiego jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="22854-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22854-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22854-112">Requirements</span></span>  
 <span data-ttu-id="22854-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22854-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22854-114">**Nagłówki** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="22854-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="22854-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22854-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22854-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22854-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22854-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22854-117">See also</span></span>

- [<span data-ttu-id="22854-118">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="22854-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="22854-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="22854-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="22854-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="22854-120">Debugging</span></span>](index.md)
