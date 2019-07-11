---
title: COR_PRF_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57520b4a67eb164c8f8631dc4d63d32c655dafa2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753823"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="1279c-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="1279c-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="1279c-103">Udostępnia reprezentację unikatową funkcję, łącząc się jego Identyfikatorem jego ponownej kompilacji wersji.</span><span class="sxs-lookup"><span data-stu-id="1279c-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1279c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1279c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="1279c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1279c-105">Members</span></span>  
  
|<span data-ttu-id="1279c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1279c-106">Member</span></span>|<span data-ttu-id="1279c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1279c-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="1279c-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="1279c-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="1279c-109">Identyfikator funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1279c-109">The ID of the recompiled function.</span></span> <span data-ttu-id="1279c-110">Wartość 0 (zero) reprezentuje oryginalną wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="1279c-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1279c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1279c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1279c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1279c-112">Requirements</span></span>  
 <span data-ttu-id="1279c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1279c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1279c-114">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1279c-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1279c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1279c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1279c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1279c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1279c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1279c-117">See also</span></span>

- [<span data-ttu-id="1279c-118">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="1279c-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
