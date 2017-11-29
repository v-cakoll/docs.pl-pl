---
title: "StackOverflowInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 102f744ecc769a10161cd20767e8e49c838252a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="e2634-102">StackOverflowInfo — Struktura</span><span class="sxs-lookup"><span data-stu-id="e2634-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="e2634-103">Przechowuje typ i przepełnienia, który wystąpił na wyjątek zgłoszony z powodu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="e2634-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2634-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2634-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e2634-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e2634-105">Members</span></span>  
  
|<span data-ttu-id="e2634-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e2634-106">Member</span></span>|<span data-ttu-id="e2634-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e2634-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="e2634-108">Wartość [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) wyliczenia, która określa typ przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="e2634-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="e2634-109">Wskaźnik do Win32 `EXCEPTION_POINTERS` obiekt, który zawiera rekord wyjątku z opisem wyjątku niezależne od komputera i rekordu kontekstu z opisem zależne od maszyny kontekst procesora w czasie wystąpienia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e2634-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2634-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2634-110">Remarks</span></span>  
 <span data-ttu-id="e2634-111">A `StackOverflowInfo` obiekt jest przekazywany do [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę `Event_StackOverflow` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e2634-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2634-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2634-112">Requirements</span></span>  
 <span data-ttu-id="e2634-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2634-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2634-114">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e2634-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e2634-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2634-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2634-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2634-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2634-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2634-117">See Also</span></span>  
 [<span data-ttu-id="e2634-118">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="e2634-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
