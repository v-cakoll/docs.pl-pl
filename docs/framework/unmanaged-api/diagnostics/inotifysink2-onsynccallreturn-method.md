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
ms.openlocfilehash: d2d90d33ce7a8135f40a0fb4039a2418dd1987ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435971"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="4f668-102">INotifySink2::OnSyncCallReturn — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f668-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="4f668-103">Gets invoked when a call returns.</span><span class="sxs-lookup"><span data-stu-id="4f668-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f668-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f668-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f668-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f668-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="4f668-106">[in] ID of the call being returned from.</span><span class="sxs-lookup"><span data-stu-id="4f668-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="4f668-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="4f668-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="4f668-108">[in] Call buffer.</span><span class="sxs-lookup"><span data-stu-id="4f668-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="4f668-109">[in] Size of the call buffer, in bytes.</span><span class="sxs-lookup"><span data-stu-id="4f668-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f668-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4f668-110">Return Value</span></span>  
 <span data-ttu-id="4f668-111">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="4f668-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f668-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f668-112">Requirements</span></span>  
 <span data-ttu-id="4f668-113">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="4f668-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f668-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f668-114">See also</span></span>

- [<span data-ttu-id="4f668-115">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f668-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="4f668-116">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f668-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="4f668-117">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f668-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
