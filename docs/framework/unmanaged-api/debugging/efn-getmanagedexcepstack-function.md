---
title: _EFN_GetManagedExcepStack — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44f3604e3c12cd4b9781876d2d412d942353061e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404157"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="e6a59-102">_EFN_GetManagedExcepStack — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e6a59-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="e6a59-103">Podany adres obiektu zarządzanym wyjątku zwraca ciąg wersji śladu stosu znajdująca się wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="e6a59-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6a59-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6a59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6a59-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="e6a59-106">[in] Klient debugowany.</span><span class="sxs-lookup"><span data-stu-id="e6a59-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="e6a59-107">[in] Wskaźnik do obiektu zarządzanego, pochodzących z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e6a59-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="e6a59-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="e6a59-108">szStackString</span></span>  
 <span data-ttu-id="e6a59-109">[out] Zwracany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e6a59-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="e6a59-110">[out] Liczba dostępnych w buforze ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="e6a59-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6a59-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6a59-111">Remarks</span></span>  
 <span data-ttu-id="e6a59-112">Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartości instrumentu 0xa0 i błąd o kodzie 0x1000.</span><span class="sxs-lookup"><span data-stu-id="e6a59-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6a59-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6a59-113">Requirements</span></span>  
 <span data-ttu-id="e6a59-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a59-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6a59-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="e6a59-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="e6a59-116">**.NET framework w wersji:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6a59-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a59-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6a59-117">See Also</span></span>  
 [<span data-ttu-id="e6a59-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="e6a59-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
