---
title: "IMethodMalloc — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="eb6b9-102">IMethodMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eb6b9-102">IMethodMalloc Interface</span></span>
<span data-ttu-id="eb6b9-103">Udostępnia metodę można przydzielić pamięci dla nowego treści funkcji języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-103">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb6b9-104">`IMethodMalloc` Interfejs jest proste alokatora.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-104">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="eb6b9-105">Można przydzielić pamięci, ale nie do jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-105">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb6b9-106">Metody</span><span class="sxs-lookup"><span data-stu-id="eb6b9-106">Methods</span></span>  
  
|<span data-ttu-id="eb6b9-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb6b9-107">Method</span></span>|<span data-ttu-id="eb6b9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="eb6b9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb6b9-109">ALLOC — metoda</span><span class="sxs-lookup"><span data-stu-id="eb6b9-109">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|<span data-ttu-id="eb6b9-110">Próbuje przydzielić określonej ilości pamięci dla nowego treści funkcji MSIL.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-110">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb6b9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb6b9-111">Remarks</span></span>  
 <span data-ttu-id="eb6b9-112">Każdy program przydzielania jest zależna od modułu i będzie treści funkcji z przesunięciem dodatnią od podstawy modułu.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-112">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="eb6b9-113">Pamięć od podstawy modułu można cenny, więc program przydzielania należy przydzielić pamięci tylko dla treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="eb6b9-113">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb6b9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb6b9-114">Requirements</span></span>  
 <span data-ttu-id="eb6b9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb6b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6b9-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb6b9-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb6b9-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb6b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb6b9-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6b9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb6b9-119">See Also</span></span>  
 [<span data-ttu-id="eb6b9-120">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="eb6b9-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
