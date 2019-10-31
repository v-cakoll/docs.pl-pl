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
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123008"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="3a462-102">\_EFN\_funkcja GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="3a462-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="3a462-103">Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3a462-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a462-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a462-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a462-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a462-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="3a462-106">podczas Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="3a462-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="3a462-107">podczas Wskaźnik obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3a462-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="3a462-108">szName</span><span class="sxs-lookup"><span data-stu-id="3a462-108">szName</span></span>  
 <span data-ttu-id="3a462-109">określoną Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="3a462-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="3a462-110">określoną Liczba znaków dostępnych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="3a462-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a462-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a462-111">Remarks</span></span>  
 <span data-ttu-id="3a462-112">W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca wartość HRESULT SOS_E_NOMANAGEDCODE z wartością instrumentu 0xa0 i kod błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="3a462-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a462-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a462-113">Requirements</span></span>  
 <span data-ttu-id="3a462-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a462-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a462-115">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="3a462-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="3a462-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a462-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a462-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a462-117">See also</span></span>

- [<span data-ttu-id="3a462-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="3a462-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
