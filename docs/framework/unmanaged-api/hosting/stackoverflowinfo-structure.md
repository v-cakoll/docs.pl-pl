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
ms.openlocfilehash: 7de5a6d38d43c20ce52f609ef6514a1f28022416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781135"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="77daf-102">StackOverflowInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="77daf-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="77daf-103">Typ przepełnienia, które wystąpiły, oraz informacje są przechowywane na wyjątek, który został wygenerowany z powodu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="77daf-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77daf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77daf-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="77daf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="77daf-105">Members</span></span>  
  
|<span data-ttu-id="77daf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="77daf-106">Member</span></span>|<span data-ttu-id="77daf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="77daf-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="77daf-108">Wartość [stackoverflowtype —](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) wyliczenie, który określa typ przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="77daf-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="77daf-109">Wskaźnik do systemu Win32 `EXCEPTION_POINTERS` obiekt, który zawiera rekord wyjątku z opisem wyjątku niezależne od komputera i rekordu kontekstu z opisem zależnych od maszyny kontekst procesora w czasie wystąpienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="77daf-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77daf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77daf-110">Remarks</span></span>  
 <span data-ttu-id="77daf-111">A `StackOverflowInfo` obiekt jest przekazywany do [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę `Event_StackOverflow` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="77daf-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77daf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77daf-112">Requirements</span></span>  
 <span data-ttu-id="77daf-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77daf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77daf-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="77daf-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="77daf-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77daf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77daf-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77daf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77daf-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77daf-117">See also</span></span>

- [<span data-ttu-id="77daf-118">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="77daf-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
