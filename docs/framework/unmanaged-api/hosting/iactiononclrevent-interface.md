---
title: IActionOnCLREvent — Interfejs
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: f577e9252d97ec188ff1076fd8340336b16c8257
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504332"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="4ab0c-102">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4ab0c-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="4ab0c-103">Udostępnia metodę [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) , która wykonuje wywołania zwrotne dla zdarzeń, które zostały zarejestrowane przy użyciu wywołania metody [ICLROnEventManager:: RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4ab0c-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ab0c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4ab0c-104">Methods</span></span>  
  
|<span data-ttu-id="4ab0c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4ab0c-105">Method</span></span>|<span data-ttu-id="4ab0c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4ab0c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ab0c-107">OnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="4ab0c-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="4ab0c-108">Wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4ab0c-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ab0c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ab0c-109">Requirements</span></span>  
 <span data-ttu-id="4ab0c-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab0c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab0c-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ab0c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ab0c-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ab0c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab0c-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab0c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab0c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ab0c-114">See also</span></span>

- [<span data-ttu-id="4ab0c-115">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ab0c-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="4ab0c-116">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4ab0c-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4ab0c-117">ICLROnEventManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ab0c-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="4ab0c-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4ab0c-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
