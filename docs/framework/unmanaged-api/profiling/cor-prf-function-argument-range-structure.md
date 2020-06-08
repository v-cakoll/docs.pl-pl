---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
ms.openlocfilehash: 8b3785955ec138bbf898e84aa4deb5ed2a6e6b53
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500952"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="22e39-102">COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="22e39-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="22e39-103">Reprezentuje blok argumentów funkcji przechowywanych w sposób ciągły w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="22e39-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22e39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22e39-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="22e39-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22e39-105">Members</span></span>  
  
|<span data-ttu-id="22e39-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22e39-106">Members</span></span>|<span data-ttu-id="22e39-107">Opis</span><span class="sxs-lookup"><span data-stu-id="22e39-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="22e39-108">Adres początkowy bloku.</span><span class="sxs-lookup"><span data-stu-id="22e39-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="22e39-109">Długość bloku ciągłego.</span><span class="sxs-lookup"><span data-stu-id="22e39-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22e39-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22e39-110">Requirements</span></span>  
 <span data-ttu-id="22e39-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22e39-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22e39-112">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="22e39-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="22e39-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="22e39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22e39-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e39-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22e39-115">See also</span></span>

- [<span data-ttu-id="22e39-116">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="22e39-116">Profiling Structures</span></span>](profiling-structures.md)
