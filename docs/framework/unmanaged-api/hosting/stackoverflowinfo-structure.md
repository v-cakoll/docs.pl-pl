---
title: StackOverflowInfo — Struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105920"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="88a71-102">StackOverflowInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="88a71-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="88a71-103">Przechowuje typ przepełnienia, który wystąpił, i informacje o wyjątku, który został zgłoszony z powodu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="88a71-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88a71-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="88a71-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="88a71-105">Members</span></span>  
  
|<span data-ttu-id="88a71-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="88a71-106">Member</span></span>|<span data-ttu-id="88a71-107">Opis</span><span class="sxs-lookup"><span data-stu-id="88a71-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="88a71-108">Wartość wyliczenia [StackOverflowType —](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) , która określa typ przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="88a71-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="88a71-109">Wskaźnik do obiektu Win32 `EXCEPTION_POINTERS`, który zawiera rekord wyjątku z niezależnym od maszyny opis wyjątku i rekordu kontekstu z zależnością od maszyny w momencie wystąpienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="88a71-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88a71-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88a71-110">Remarks</span></span>  
 <span data-ttu-id="88a71-111">Obiekt `StackOverflowInfo` jest przenoszona do metody [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) dla zdarzeń `Event_StackOverflow`.</span><span class="sxs-lookup"><span data-stu-id="88a71-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a71-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88a71-112">Requirements</span></span>  
 <span data-ttu-id="88a71-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88a71-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a71-114">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="88a71-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="88a71-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88a71-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88a71-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88a71-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a71-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88a71-117">See also</span></span>

- [<span data-ttu-id="88a71-118">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="88a71-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
