---
title: "INotifyConnection2::UnregisterNotifySource — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.UnregisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063a146d31031f0cb14e00278819e8cd874f98c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="6588f-102">INotifyConnection2::UnregisterNotifySource — Metoda</span><span class="sxs-lookup"><span data-stu-id="6588f-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="6588f-103">Usuwa obiekt źródłowy określony powiadomień z połączenia.</span><span class="sxs-lookup"><span data-stu-id="6588f-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6588f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6588f-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6588f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6588f-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="6588f-106">[in] Obiekt powiadomienia do wyrejestrowania.</span><span class="sxs-lookup"><span data-stu-id="6588f-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6588f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6588f-107">Return Value</span></span>  
 <span data-ttu-id="6588f-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6588f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6588f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6588f-109">Requirements</span></span>  
 <span data-ttu-id="6588f-110">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6588f-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6588f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6588f-111">See Also</span></span>  
 [<span data-ttu-id="6588f-112">INotifyConnection2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6588f-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="6588f-113">INotifySource2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6588f-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="6588f-114">INotifySink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6588f-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="6588f-115">RegisterNotifySource — metoda</span><span class="sxs-lookup"><span data-stu-id="6588f-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
