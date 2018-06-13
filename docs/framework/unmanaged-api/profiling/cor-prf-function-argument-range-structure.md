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
ms.openlocfilehash: 92e3a0a930a4e4b91cac27cbed1b745dea4207a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450027"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="ceb58-102">COR_PRF_FUNCTION_ARGUMENT_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="ceb58-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="ceb58-103">Reprezentuje blok argumentów funkcji ciągłym przechowywane w kolejności od lewej do prawej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ceb58-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ceb58-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="ceb58-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ceb58-105">Members</span></span>  
  
|<span data-ttu-id="ceb58-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ceb58-106">Members</span></span>|<span data-ttu-id="ceb58-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb58-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="ceb58-108">Adres początkowy bloku.</span><span class="sxs-lookup"><span data-stu-id="ceb58-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="ceb58-109">Długość ciągłego bloku.</span><span class="sxs-lookup"><span data-stu-id="ceb58-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceb58-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ceb58-110">Requirements</span></span>  
 <span data-ttu-id="ceb58-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceb58-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceb58-112">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ceb58-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ceb58-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ceb58-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ceb58-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceb58-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb58-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ceb58-115">See Also</span></span>  
 [<span data-ttu-id="ceb58-116">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="ceb58-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
