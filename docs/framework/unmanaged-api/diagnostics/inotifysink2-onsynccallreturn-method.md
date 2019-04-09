---
title: INotifySink2::OnSyncCallReturn — Metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0adc6ec1db3f12d1850bb6ff9a01d5b6cc5f90c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157927"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="9874d-102">INotifySink2::OnSyncCallReturn — Metoda</span><span class="sxs-lookup"><span data-stu-id="9874d-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="9874d-103">Pobiera wywoływane, gdy wywołanie zwraca.</span><span class="sxs-lookup"><span data-stu-id="9874d-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9874d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9874d-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9874d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9874d-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="9874d-106">[in] Identyfikator wywołania zwracanego.</span><span class="sxs-lookup"><span data-stu-id="9874d-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="9874d-107">Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="9874d-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="9874d-108">[in] Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="9874d-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="9874d-109">[in] Rozmiar buforu wywołania, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9874d-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9874d-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9874d-110">Return Value</span></span>  
 <span data-ttu-id="9874d-111">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9874d-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9874d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9874d-112">Requirements</span></span>  
 <span data-ttu-id="9874d-113">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9874d-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9874d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9874d-114">See also</span></span>

- [<span data-ttu-id="9874d-115">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9874d-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="9874d-116">INotifySource2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9874d-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="9874d-117">INotifyConnection2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9874d-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
