---
title: _EFN_GetManagedObjectName — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eddb1461ad448a1a1718db8a11173e5e2e4a17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527786"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="13226-102">_EFN_GetManagedObjectName — Funkcja</span><span class="sxs-lookup"><span data-stu-id="13226-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="13226-103">Pobiera nazwę typu przy użyciu wskaźnika udostępnionego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="13226-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13226-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13226-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13226-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13226-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="13226-106">[in] Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="13226-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="13226-107">[in] Wskaźnik zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="13226-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="13226-108">szName</span><span class="sxs-lookup"><span data-stu-id="13226-108">szName</span></span>  
 <span data-ttu-id="13226-109">[out] Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="13226-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="13226-110">[out] Liczba dostępnych w buforu ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="13226-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13226-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13226-111">Remarks</span></span>  
 <span data-ttu-id="13226-112">Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="13226-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13226-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13226-113">Requirements</span></span>  
 <span data-ttu-id="13226-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13226-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13226-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="13226-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="13226-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13226-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13226-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13226-117">See also</span></span>
- [<span data-ttu-id="13226-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="13226-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
