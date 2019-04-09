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
ms.openlocfilehash: 7e201b9a350c030da59e2b6ed27f84f570c8e621
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126662"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="9a6b8-102">_EFN_GetManagedExcepStack — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a6b8-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="9a6b8-103">Podany adres obiektu zarządzanego wyjątku zwraca wersję ślad stosu zawarte wewnątrz ciągu.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a6b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a6b8-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a6b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a6b8-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="9a6b8-106">[in] Klient debugowane.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="9a6b8-107">[in] Wskaźnik do obiektu zarządzanego, pochodzące z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="9a6b8-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="9a6b8-108">szStackString</span></span>  
 <span data-ttu-id="9a6b8-109">[out] Zwracanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="9a6b8-110">[out] Liczba dostępnych w buforu ciągu znaków.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a6b8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a6b8-111">Remarks</span></span>  
 <span data-ttu-id="9a6b8-112">Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="9a6b8-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a6b8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a6b8-113">Requirements</span></span>  
 <span data-ttu-id="9a6b8-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a6b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a6b8-115">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="9a6b8-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="9a6b8-116">Wersja programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a6b8-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a6b8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a6b8-117">See also</span></span>

- [<span data-ttu-id="9a6b8-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="9a6b8-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
