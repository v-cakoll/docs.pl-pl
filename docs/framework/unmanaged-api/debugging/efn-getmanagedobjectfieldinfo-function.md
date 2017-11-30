---
title: "_EFN_GetManagedObjectFieldInfo — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectFieldInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectFieldInfo
helpviewer_keywords: _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3df09c9107b683381f21891a1001140c493a024
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="53929-102">_EFN_GetManagedObjectFieldInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="53929-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="53929-103">Pobiera przesunięcie od początku obiektu, do pola i wartość do pola, używając udostępnionego obiektu wskaźnik i nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="53929-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53929-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53929-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53929-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53929-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="53929-106">[in] Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="53929-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="53929-107">[in] Wskaźnik do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="53929-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="53929-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="53929-108">szFieldName</span></span>  
 <span data-ttu-id="53929-109">[in] Wskaźnik do obiektu zarządzanego, nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="53929-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="53929-110">[out] Wartość pola.</span><span class="sxs-lookup"><span data-stu-id="53929-110">[out] The field value.</span></span> <span data-ttu-id="53929-111">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="53929-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="53929-112">[out] Przesunięcie od `objAddr` do pola.</span><span class="sxs-lookup"><span data-stu-id="53929-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="53929-113">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="53929-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53929-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53929-114">Remarks</span></span>  
 <span data-ttu-id="53929-115">Jeśli przesunięcie wynosi 0, przesunięcie nie są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="53929-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="53929-116">Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartości instrumentu 0xa0 i błąd o kodzie 0x1000.</span><span class="sxs-lookup"><span data-stu-id="53929-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53929-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53929-117">Requirements</span></span>  
 <span data-ttu-id="53929-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53929-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53929-119">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="53929-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="53929-120">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53929-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53929-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53929-121">See Also</span></span>  
 [<span data-ttu-id="53929-122">Statyczne funkcje globalne debugowania</span><span class="sxs-lookup"><span data-stu-id="53929-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
