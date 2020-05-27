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
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006522"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="a133b-102">StackOverflowInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="a133b-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="a133b-103">Przechowuje typ przepełnienia, który wystąpił, i informacje o wyjątku, który został zgłoszony z powodu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="a133b-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a133b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a133b-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="a133b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a133b-105">Members</span></span>  
  
|<span data-ttu-id="a133b-106">Członek</span><span class="sxs-lookup"><span data-stu-id="a133b-106">Member</span></span>|<span data-ttu-id="a133b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a133b-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="a133b-108">Wartość wyliczenia [StackOverflowType —](stackoverflowtype-enumeration.md) , która określa typ przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="a133b-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="a133b-109">Wskaźnik do `EXCEPTION_POINTERS` obiektu Win32, który zawiera rekord wyjątku z niezależnym od maszyny opisem wyjątku i rekordu kontekstu z opisem zależnym od maszyny w momencie wystąpienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a133b-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a133b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a133b-110">Remarks</span></span>  
 <span data-ttu-id="a133b-111">`StackOverflowInfo`Obiekt jest przesyłany do metody [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) dla `Event_StackOverflow` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a133b-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a133b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a133b-112">Requirements</span></span>  
 <span data-ttu-id="a133b-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a133b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a133b-114">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="a133b-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a133b-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a133b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a133b-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a133b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a133b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a133b-117">See also</span></span>

- [<span data-ttu-id="a133b-118">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="a133b-118">Hosting Structures</span></span>](hosting-structures.md)
