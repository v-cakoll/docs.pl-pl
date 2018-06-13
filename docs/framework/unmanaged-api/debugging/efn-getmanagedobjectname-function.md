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
ms.openlocfilehash: 9f13fad537a6847ba6e19c939e72df86036e28ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402207"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="23662-102">_EFN_GetManagedObjectName — Funkcja</span><span class="sxs-lookup"><span data-stu-id="23662-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="23662-103">Pobiera nazwę typu przy użyciu wskaźnika podanego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="23662-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23662-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23662-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23662-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23662-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="23662-106">[in] Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="23662-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="23662-107">[in] Wskaźnik do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="23662-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="23662-108">szName</span><span class="sxs-lookup"><span data-stu-id="23662-108">szName</span></span>  
 <span data-ttu-id="23662-109">[out] Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="23662-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="23662-110">[out] Liczba dostępnych w buforze ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="23662-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23662-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23662-111">Remarks</span></span>  
 <span data-ttu-id="23662-112">Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartości instrumentu 0xa0 i błąd o kodzie 0x1000.</span><span class="sxs-lookup"><span data-stu-id="23662-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23662-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23662-113">Requirements</span></span>  
 <span data-ttu-id="23662-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23662-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23662-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="23662-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="23662-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23662-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23662-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23662-117">See Also</span></span>  
 [<span data-ttu-id="23662-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="23662-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
