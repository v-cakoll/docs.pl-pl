---
title: "INotifySink2::OnSyncCallExit — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43139e8be9a1f5dfb6513f2ee7768237ae882c69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="bd557-102">INotifySink2::OnSyncCallExit — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd557-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="bd557-103">Pobiera wywoływane podczas zamykania wywołania.</span><span class="sxs-lookup"><span data-stu-id="bd557-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd557-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd557-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd557-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd557-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="bd557-106">[in] Identyfikator wywołania jest zakończony.</span><span class="sxs-lookup"><span data-stu-id="bd557-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="bd557-107">Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="bd557-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="bd557-108">[out] Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="bd557-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="bd557-109">[out] Rozmiar buforu wywołanie, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bd557-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd557-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd557-110">Return Value</span></span>  
 <span data-ttu-id="bd557-111">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bd557-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd557-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd557-112">Requirements</span></span>  
 <span data-ttu-id="bd557-113">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="bd557-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd557-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd557-114">See Also</span></span>  
 [<span data-ttu-id="bd557-115">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd557-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="bd557-116">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd557-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="bd557-117">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd557-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
