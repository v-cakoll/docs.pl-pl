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
ms.openlocfilehash: 61f4e057a487462feb385ca0e3ca977fdd165f56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739092"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="f18e2-102">\_EFN\_GetManagedExcepStack Function</span><span class="sxs-lookup"><span data-stu-id="f18e2-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="f18e2-103">Podany adres obiektu zarządzanego wyjątku zwraca wersję ślad stosu zawarte wewnątrz ciągu.</span><span class="sxs-lookup"><span data-stu-id="f18e2-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f18e2-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f18e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f18e2-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="f18e2-106">[in] Klient debugowane.</span><span class="sxs-lookup"><span data-stu-id="f18e2-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="f18e2-107">[in] Wskaźnik do obiektu zarządzanego, pochodzące z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="f18e2-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="f18e2-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="f18e2-108">szStackString</span></span>  
 <span data-ttu-id="f18e2-109">[out] Zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="f18e2-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="f18e2-110">[out] Liczba dostępnych w buforu ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="f18e2-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f18e2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f18e2-111">Remarks</span></span>  
 <span data-ttu-id="f18e2-112">Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="f18e2-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f18e2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f18e2-113">Requirements</span></span>  
 <span data-ttu-id="f18e2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f18e2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f18e2-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="f18e2-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="f18e2-116">**Wersja programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f18e2-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18e2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f18e2-117">See also</span></span>

- [<span data-ttu-id="f18e2-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f18e2-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
