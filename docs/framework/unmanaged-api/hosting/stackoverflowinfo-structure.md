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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac0f5d522a24394369583692f8c564254529bf13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796048"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="7e5e6-102">StackOverflowInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="7e5e6-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="7e5e6-103">Typ przepełnienia, które wystąpiły, oraz informacje są przechowywane na wyjątek, który został wygenerowany z powodu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="7e5e6-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e5e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e5e6-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="7e5e6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7e5e6-105">Members</span></span>  
  
|<span data-ttu-id="7e5e6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7e5e6-106">Member</span></span>|<span data-ttu-id="7e5e6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7e5e6-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="7e5e6-108">Wartość [stackoverflowtype —](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) wyliczenie, który określa typ przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="7e5e6-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="7e5e6-109">Wskaźnik do systemu Win32 `EXCEPTION_POINTERS` obiekt, który zawiera rekord wyjątku z opisem wyjątku niezależne od komputera i rekordu kontekstu z opisem zależnych od maszyny kontekst procesora w czasie wystąpienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7e5e6-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e5e6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e5e6-110">Remarks</span></span>  
 <span data-ttu-id="7e5e6-111">A `StackOverflowInfo` obiekt jest przekazywany do [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę `Event_StackOverflow` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7e5e6-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e5e6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e5e6-112">Requirements</span></span>  
 <span data-ttu-id="7e5e6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e5e6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e5e6-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7e5e6-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7e5e6-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e5e6-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e5e6-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e5e6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e5e6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e5e6-117">See also</span></span>

- [<span data-ttu-id="7e5e6-118">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="7e5e6-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
