---
title: INotifySink2::OnSyncCallOut — Metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf36b9e09f5e9eeb28930a6adc48426927a60e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145694"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="122d1-102">INotifySink2::OnSyncCallOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="122d1-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="122d1-103">Pobiera wywoływane, gdy wywołanie jest zewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="122d1-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="122d1-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="122d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="122d1-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="122d1-106">[in] Identyfikator połączenia, który jest zewnętrzny. Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="122d1-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="122d1-107">[out] Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="122d1-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="122d1-108">[out] Rozmiar buforu wywołania, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="122d1-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="122d1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="122d1-109">Return Value</span></span>  
 <span data-ttu-id="122d1-110">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="122d1-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122d1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="122d1-111">Requirements</span></span>  
 <span data-ttu-id="122d1-112">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="122d1-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122d1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="122d1-113">See also</span></span>

- [<span data-ttu-id="122d1-114">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="122d1-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="122d1-115">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="122d1-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="122d1-116">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="122d1-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
