---
title: INotifyConnection2::UnregisterNotifySource — Metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b8a8c3dbfb7b9949811025846484ab233ed3741
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776625"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="261fb-102">INotifyConnection2::UnregisterNotifySource — Metoda</span><span class="sxs-lookup"><span data-stu-id="261fb-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="261fb-103">Usuwa obiekt źródłowy określony powiadomień z połączenia.</span><span class="sxs-lookup"><span data-stu-id="261fb-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="261fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="261fb-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="261fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="261fb-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="261fb-106">[in] Obiekt powiadomień do wyrejestrowania.</span><span class="sxs-lookup"><span data-stu-id="261fb-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="261fb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="261fb-107">Return Value</span></span>  
 <span data-ttu-id="261fb-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="261fb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="261fb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="261fb-109">Requirements</span></span>  
 <span data-ttu-id="261fb-110">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="261fb-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261fb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="261fb-111">See also</span></span>

- [<span data-ttu-id="261fb-112">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="261fb-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="261fb-113">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="261fb-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="261fb-114">INotifySink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="261fb-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="261fb-115">RegisterNotifySource, metoda</span><span class="sxs-lookup"><span data-stu-id="261fb-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
