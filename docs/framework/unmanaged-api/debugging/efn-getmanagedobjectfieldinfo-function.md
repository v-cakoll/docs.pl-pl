---
title: _EFN_GetManagedObjectFieldInfo — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738999"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="8dfa6-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="8dfa6-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="8dfa6-103">Pobiera przesunięcie od początku obiektu, do pola i wartość do pola, używając wskaźnika udostępnionego obiektu i nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dfa6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8dfa6-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dfa6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dfa6-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8dfa6-106">[in] Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="8dfa6-107">[in] Wskaźnik zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="8dfa6-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="8dfa6-108">szFieldName</span></span>  
 <span data-ttu-id="8dfa6-109">[in] Wskaźnik do obiektu zarządzanego, do nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8dfa6-110">[out] Wartość pola.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-110">[out] The field value.</span></span> <span data-ttu-id="8dfa6-111">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="8dfa6-112">[out] Przesunięcie od `objAddr` do pola.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="8dfa6-113">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dfa6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8dfa6-114">Remarks</span></span>  
 <span data-ttu-id="8dfa6-115">Przesunięcie wynosi 0, przesunięcie nie zostanie zapisane.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="8dfa6-116">Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="8dfa6-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dfa6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8dfa6-117">Requirements</span></span>  
 <span data-ttu-id="8dfa6-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dfa6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dfa6-119">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="8dfa6-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8dfa6-120">**Wersja programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dfa6-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dfa6-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dfa6-121">See also</span></span>

- [<span data-ttu-id="8dfa6-122">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="8dfa6-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
