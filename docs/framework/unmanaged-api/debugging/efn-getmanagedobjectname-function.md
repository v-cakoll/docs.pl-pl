---
title: "_EFN_GetManagedObjectName — Funkcja"
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
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c29aa82143c34a229cee0a5b000657c9add22bd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="af383-102">_EFN_GetManagedObjectName — Funkcja</span><span class="sxs-lookup"><span data-stu-id="af383-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="af383-103">Pobiera nazwę typu przy użyciu wskaźnika podanego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="af383-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af383-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af383-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af383-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af383-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="af383-106">[in] Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="af383-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="af383-107">[in] Wskaźnik do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="af383-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="af383-108">szName</span><span class="sxs-lookup"><span data-stu-id="af383-108">szName</span></span>  
 <span data-ttu-id="af383-109">[out] Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="af383-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="af383-110">[out] Liczba dostępnych w buforze ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="af383-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af383-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af383-111">Remarks</span></span>  
 <span data-ttu-id="af383-112">Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartości instrumentu 0xa0 i błąd o kodzie 0x1000.</span><span class="sxs-lookup"><span data-stu-id="af383-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af383-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af383-113">Requirements</span></span>  
 <span data-ttu-id="af383-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af383-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af383-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="af383-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="af383-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af383-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af383-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af383-117">See Also</span></span>  
 [<span data-ttu-id="af383-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="af383-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
