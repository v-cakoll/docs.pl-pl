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
ms.openlocfilehash: 14dcb251e25b5bd502c8d514a6dc35778fbe9f73
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867233"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="47d3a-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="47d3a-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="47d3a-103">Zapewnia unikatową reprezentację funkcji przez połączenie jej identyfikatora z IDENTYFIKATORem jego ponownie skompilowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="47d3a-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47d3a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="47d3a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="47d3a-105">Members</span></span>  
  
|<span data-ttu-id="47d3a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="47d3a-106">Member</span></span>|<span data-ttu-id="47d3a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="47d3a-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="47d3a-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="47d3a-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="47d3a-109">Identyfikator ponownie skompilowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="47d3a-109">The ID of the recompiled function.</span></span> <span data-ttu-id="47d3a-110">Wartość 0 (zero) reprezentuje oryginalną wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="47d3a-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47d3a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47d3a-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d3a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47d3a-112">Requirements</span></span>  
 <span data-ttu-id="47d3a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47d3a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47d3a-114">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="47d3a-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="47d3a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="47d3a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47d3a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d3a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47d3a-117">See also</span></span>

- [<span data-ttu-id="47d3a-118">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="47d3a-118">Profiling Structures</span></span>](profiling-structures.md)
