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
ms.openlocfilehash: 708ac2e407bf6f87dbe314a0e87cdd16f45b2bcf
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860744"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="6896c-102">\_Funkcja\_EFN GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="6896c-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="6896c-103">Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6896c-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6896c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6896c-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6896c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6896c-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="6896c-106">podczas Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="6896c-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="6896c-107">podczas Wskaźnik obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6896c-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="6896c-108">szName</span><span class="sxs-lookup"><span data-stu-id="6896c-108">szName</span></span>  
 <span data-ttu-id="6896c-109">określoną Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="6896c-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="6896c-110">określoną Liczba znaków dostępnych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="6896c-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6896c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6896c-111">Remarks</span></span>  
 <span data-ttu-id="6896c-112">W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca wartość HRESULT SOS_E_NOMANAGEDCODE z wartością instrumentu 0xa0 i kodem błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="6896c-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6896c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6896c-113">Requirements</span></span>  
 <span data-ttu-id="6896c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6896c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6896c-115">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="6896c-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6896c-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6896c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6896c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6896c-117">See also</span></span>

- [<span data-ttu-id="6896c-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="6896c-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
