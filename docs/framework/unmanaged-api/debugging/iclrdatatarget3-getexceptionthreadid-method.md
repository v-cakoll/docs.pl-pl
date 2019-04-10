---
title: Metoda ICLRDataTarget3::GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215303"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="92638-102">Metoda ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="92638-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="92638-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) usługi dostępu do danych można uzyskać identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="92638-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92638-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92638-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92638-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92638-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="92638-106">[out] Identyfikator wątku, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="92638-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92638-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92638-107">Return Value</span></span>  
 <span data-ttu-id="92638-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="92638-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="92638-109">`HRESULT` Mogą obejmować kody, ale nie są ograniczone do następujących:</span><span class="sxs-lookup"><span data-stu-id="92638-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="92638-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="92638-110">Return code</span></span>|<span data-ttu-id="92638-111">Opis</span><span class="sxs-lookup"><span data-stu-id="92638-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="92638-112">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="92638-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="92638-113">Nie można odnaleźć Identyfikatora wątku prawidłowy dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="92638-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92638-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92638-114">Remarks</span></span>  
 <span data-ttu-id="92638-115">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92638-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92638-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92638-116">Requirements</span></span>  
 <span data-ttu-id="92638-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92638-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92638-118">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="92638-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="92638-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92638-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="92638-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="92638-120">.NET Framework Versions:</span></span>** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92638-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92638-121">See also</span></span>

- [<span data-ttu-id="92638-122">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="92638-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="92638-123">GetExceptionContextRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="92638-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="92638-124">GetExceptionRecord, metoda</span><span class="sxs-lookup"><span data-stu-id="92638-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
