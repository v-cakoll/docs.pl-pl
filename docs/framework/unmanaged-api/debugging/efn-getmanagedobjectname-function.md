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
ms.openlocfilehash: 9230e1fcba7c0492e50773e7ca13fb16f07238a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789135"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="ab32a-102">\_EFN\_funkcja GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="ab32a-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="ab32a-103">Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ab32a-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab32a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab32a-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab32a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab32a-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ab32a-106">podczas Wskaźnik do klienta debugowania.</span><span class="sxs-lookup"><span data-stu-id="ab32a-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="ab32a-107">podczas Wskaźnik obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ab32a-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="ab32a-108">szName</span><span class="sxs-lookup"><span data-stu-id="ab32a-108">szName</span></span>  
 <span data-ttu-id="ab32a-109">określoną Nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="ab32a-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="ab32a-110">określoną Liczba znaków dostępnych w buforze ciągów.</span><span class="sxs-lookup"><span data-stu-id="ab32a-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab32a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab32a-111">Remarks</span></span>  
 <span data-ttu-id="ab32a-112">W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca wartość HRESULT SOS_E_NOMANAGEDCODE z wartością instrumentu 0xa0 i kodem błędu 0x1000.</span><span class="sxs-lookup"><span data-stu-id="ab32a-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab32a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab32a-113">Requirements</span></span>  
 <span data-ttu-id="ab32a-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab32a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab32a-115">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="ab32a-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ab32a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab32a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab32a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab32a-117">See also</span></span>

- [<span data-ttu-id="ab32a-118">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ab32a-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
