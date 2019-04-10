---
title: INotifySink2::OnSyncCallEnter — Metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78aaa5d8031e7b554eee2a147d9940ff8d7f7e02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201900"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="6af02-102">INotifySink2::OnSyncCallEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="6af02-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="6af02-103">Pobiera element wywoływany w przypadku wprowadzania wywołanie.</span><span class="sxs-lookup"><span data-stu-id="6af02-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6af02-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6af02-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="6af02-106">[in] Identyfikator wywołania wprowadzanych.</span><span class="sxs-lookup"><span data-stu-id="6af02-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="6af02-107">Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6af02-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="6af02-108">[in] Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="6af02-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="6af02-109">[in] Rozmiar buforu wywołania, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6af02-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6af02-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6af02-110">Return Value</span></span>  
 <span data-ttu-id="6af02-111">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6af02-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af02-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6af02-112">Requirements</span></span>  
 <span data-ttu-id="6af02-113">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6af02-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af02-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6af02-114">See also</span></span>

- [<span data-ttu-id="6af02-115">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6af02-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="6af02-116">INotifySource2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6af02-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="6af02-117">INotifyConnection2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6af02-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
