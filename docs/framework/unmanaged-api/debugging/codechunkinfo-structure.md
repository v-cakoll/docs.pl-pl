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
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132398"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="be47a-102">CodeChunkInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="be47a-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="be47a-103">Reprezentuje pojedynczy fragment kodu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="be47a-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be47a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be47a-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="be47a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="be47a-105">Members</span></span>  
  
|<span data-ttu-id="be47a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="be47a-106">Member</span></span>|<span data-ttu-id="be47a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="be47a-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="be47a-108">Wartość `CORDB_ADDRESS`, która określa adres początkowy fragmentu.</span><span class="sxs-lookup"><span data-stu-id="be47a-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="be47a-109">Rozmiar fragmentu, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="be47a-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be47a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be47a-110">Remarks</span></span>  
 <span data-ttu-id="be47a-111">Pojedynczy fragment kodu jest regionem kodu natywnego, który jest częścią obiektu kodu, takiego jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="be47a-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be47a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be47a-112">Requirements</span></span>  
 <span data-ttu-id="be47a-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be47a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be47a-114">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="be47a-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="be47a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be47a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be47a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be47a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be47a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be47a-117">See also</span></span>

- [<span data-ttu-id="be47a-118">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="be47a-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="be47a-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="be47a-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="be47a-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="be47a-120">Debugging</span></span>](index.md)
