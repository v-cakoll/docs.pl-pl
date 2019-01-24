---
title: INotifySink2 — Interfejs
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc5d09ac12919b8c68b9fe4bf9f7dc0009b2d4b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705472"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="4f3fa-102">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4f3fa-102">INotifySink2 Interface</span></span>
<span data-ttu-id="4f3fa-103">Deklaruje metody dla obiektu sink powiadomień.</span><span class="sxs-lookup"><span data-stu-id="4f3fa-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f3fa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4f3fa-104">Methods</span></span>  
  
|<span data-ttu-id="4f3fa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4f3fa-105">Method</span></span>|<span data-ttu-id="4f3fa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4f3fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f3fa-107">OnSyncCallEnter, metoda</span><span class="sxs-lookup"><span data-stu-id="4f3fa-107">OnSyncCallEnter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="4f3fa-108">Pobiera element wywoływany w przypadku wprowadzania wywołanie.</span><span class="sxs-lookup"><span data-stu-id="4f3fa-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="4f3fa-109">OnSyncCallExit, metoda</span><span class="sxs-lookup"><span data-stu-id="4f3fa-109">OnSyncCallExit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="4f3fa-110">Pobiera wywoływane podczas zamykania połączenia.</span><span class="sxs-lookup"><span data-stu-id="4f3fa-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="4f3fa-111">OnSyncCallOut, metoda</span><span class="sxs-lookup"><span data-stu-id="4f3fa-111">OnSyncCallOut Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|<span data-ttu-id="4f3fa-112">Pobiera wywoływane, gdy wywołanie jest zewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="4f3fa-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="4f3fa-113">OnSyncCallReturn, metoda</span><span class="sxs-lookup"><span data-stu-id="4f3fa-113">OnSyncCallReturn Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="4f3fa-114">Pobiera wywoływane, gdy wywołanie zwraca.</span><span class="sxs-lookup"><span data-stu-id="4f3fa-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f3fa-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f3fa-115">Requirements</span></span>  
 <span data-ttu-id="4f3fa-116">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="4f3fa-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3fa-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f3fa-117">See also</span></span>
- [<span data-ttu-id="4f3fa-118">INotifyConnection2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f3fa-118">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="4f3fa-119">INotifySource2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f3fa-119">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="4f3fa-120">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4f3fa-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
