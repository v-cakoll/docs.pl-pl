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
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789154"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="be993-102">\_EFN\_GetManagedExcepStack Function</span><span class="sxs-lookup"><span data-stu-id="be993-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="be993-103">Dany adres obiektu wyjątku zarządzanego zwraca wersję ciągu śledzenia stosu zawartych wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="be993-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be993-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be993-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be993-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="be993-106">podczas Debugowany klient.</span><span class="sxs-lookup"><span data-stu-id="be993-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="be993-107">podczas Wskaźnik obiektu zarządzanego pochodzący z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="be993-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="be993-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="be993-108">szStackString</span></span>  
 <span data-ttu-id="be993-109">określoną Zwrócony ciąg.</span><span class="sxs-lookup"><span data-stu-id="be993-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="be993-110">określoną Liczba znaków dostępnych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="be993-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be993-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be993-111">Remarks</span></span>  
 <span data-ttu-id="be993-112">W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca wartość HRESULT SOS_E_NOMANAGEDCODE z wartością instrumentu 0xa0 i kodem błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="be993-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be993-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be993-113">Requirements</span></span>  
 <span data-ttu-id="be993-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be993-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be993-115">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="be993-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="be993-116">**Wersja .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be993-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be993-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be993-117">See also</span></span>

- [<span data-ttu-id="be993-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="be993-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
