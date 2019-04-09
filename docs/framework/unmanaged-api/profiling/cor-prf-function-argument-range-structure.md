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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dffefedf14d5f219736e429be191021b2de7ddd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125596"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="c5d22-102">COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="c5d22-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="c5d22-103">Reprezentuje blok argumentów funkcji, przechowywane w sposób ciągły w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c5d22-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d22-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5d22-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="c5d22-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c5d22-105">Members</span></span>  
  
|<span data-ttu-id="c5d22-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c5d22-106">Members</span></span>|<span data-ttu-id="c5d22-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c5d22-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="c5d22-108">Początkowy adres bloku.</span><span class="sxs-lookup"><span data-stu-id="c5d22-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="c5d22-109">Długość ciągłym bloku.</span><span class="sxs-lookup"><span data-stu-id="c5d22-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5d22-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5d22-110">Requirements</span></span>  
 <span data-ttu-id="c5d22-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d22-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d22-112">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c5d22-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c5d22-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5d22-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c5d22-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c5d22-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5d22-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5d22-115">See also</span></span>

- [<span data-ttu-id="c5d22-116">Profiling — Struktury</span><span class="sxs-lookup"><span data-stu-id="c5d22-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
