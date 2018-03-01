---
title: "IMethodMalloc — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="c83bf-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c83bf-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="c83bf-103">Udostępnia metodę można przydzielić pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c83bf-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c83bf-104">`IMethodMalloc` Interfejs jest proste alokatora.</span><span class="sxs-lookup"><span data-stu-id="c83bf-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="c83bf-105">Można przydzielić pamięci, ale nie do jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="c83bf-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c83bf-106">Metody</span><span class="sxs-lookup"><span data-stu-id="c83bf-106">Methods</span></span>  
  
|<span data-ttu-id="c83bf-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="c83bf-107">Method</span></span>|<span data-ttu-id="c83bf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c83bf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c83bf-109">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="c83bf-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="c83bf-110">Próbuje przydzielić określonej ilości pamięci dla nowego treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="c83bf-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c83bf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c83bf-111">Remarks</span></span>  
 <span data-ttu-id="c83bf-112">Każdy program przydzielania jest zależna od modułu i będzie treści funkcji z przesunięciem dodatnią od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="c83bf-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="c83bf-113">Pamięć od podstawy modułu można cenny, więc program przydzielania należy przydzielić pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="c83bf-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83bf-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c83bf-114">Requirements</span></span>  
 <span data-ttu-id="c83bf-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c83bf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c83bf-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c83bf-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c83bf-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c83bf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c83bf-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c83bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83bf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c83bf-119">See Also</span></span>  
 [<span data-ttu-id="c83bf-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c83bf-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
