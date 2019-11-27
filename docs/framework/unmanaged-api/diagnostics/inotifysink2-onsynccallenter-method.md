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
ms.openlocfilehash: 69c7e6c465de5b8185a86b3de6e5c29f902a1d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440866"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="dabff-102">INotifySink2::OnSyncCallEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="dabff-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="dabff-103">Wywoływana podczas wprowadzania wywołania.</span><span class="sxs-lookup"><span data-stu-id="dabff-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dabff-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dabff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dabff-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="dabff-106">podczas Identyfikator wprowadzonego wywołania.</span><span class="sxs-lookup"><span data-stu-id="dabff-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="dabff-107">Zobacz [strukturę CALL_ID](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="dabff-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="dabff-108">podczas Bufor wywołań.</span><span class="sxs-lookup"><span data-stu-id="dabff-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="dabff-109">podczas Rozmiar buforu wywołań w bajtach.</span><span class="sxs-lookup"><span data-stu-id="dabff-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dabff-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dabff-110">Return Value</span></span>  
 <span data-ttu-id="dabff-111">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dabff-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dabff-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dabff-112">Requirements</span></span>  
 <span data-ttu-id="dabff-113">**Nagłówek:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="dabff-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabff-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dabff-114">See also</span></span>

- [<span data-ttu-id="dabff-115">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dabff-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="dabff-116">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dabff-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="dabff-117">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dabff-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
