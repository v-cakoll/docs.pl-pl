---
title: "INotifySink2::OnSyncCallOut — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallOut
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 427b54a66b92ef23572739d6c9e0dfd5731eb638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="a7e02-102">INotifySink2::OnSyncCallOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7e02-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="a7e02-103">Pobiera wywoływane, gdy połączenie jest limit.</span><span class="sxs-lookup"><span data-stu-id="a7e02-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7e02-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7e02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7e02-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="a7e02-106">[in] Identyfikator połączenia, który został przekazany. Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a7e02-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="a7e02-107">[out] Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="a7e02-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="a7e02-108">[out] Rozmiar buforu wywołanie, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7e02-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7e02-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7e02-109">Return Value</span></span>  
 <span data-ttu-id="a7e02-110">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a7e02-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e02-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7e02-111">Requirements</span></span>  
 <span data-ttu-id="a7e02-112">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a7e02-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e02-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7e02-113">See Also</span></span>  
 [<span data-ttu-id="a7e02-114">INotifySink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e02-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="a7e02-115">INotifySource2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e02-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="a7e02-116">INotifyConnection2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e02-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
