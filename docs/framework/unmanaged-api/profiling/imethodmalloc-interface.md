---
title: IMethodMalloc — Interfejs
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c67ce15175f8667139f99cec1ed17531eab473e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935646"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="db421-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db421-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="db421-103">Udostępnia metodę przydzielania pamięci dla nowej treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="db421-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db421-104">`IMethodMalloc` Interfejs jest prostym alokatorem pamięci.</span><span class="sxs-lookup"><span data-stu-id="db421-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="db421-105">Umożliwia przydzielanie pamięci, ale nie zwalnia.</span><span class="sxs-lookup"><span data-stu-id="db421-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db421-106">Metody</span><span class="sxs-lookup"><span data-stu-id="db421-106">Methods</span></span>  
  
|<span data-ttu-id="db421-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="db421-107">Method</span></span>|<span data-ttu-id="db421-108">Opis</span><span class="sxs-lookup"><span data-stu-id="db421-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db421-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="db421-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="db421-110">Próbuje przydzielić określoną ilość pamięci dla nowej treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="db421-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db421-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db421-111">Remarks</span></span>  
 <span data-ttu-id="db421-112">Każdy Alokator jest specyficzny dla modułu i gwarantuje, że treść funkcji będzie naliczona pozytywnie od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="db421-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="db421-113">Pamięć powyżej podstawy modułu może być cenna, więc Alokator powinien być używany do przydzielania pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="db421-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db421-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db421-114">Requirements</span></span>  
 <span data-ttu-id="db421-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db421-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db421-116">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="db421-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db421-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db421-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db421-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db421-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db421-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db421-119">See also</span></span>

- [<span data-ttu-id="db421-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="db421-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
