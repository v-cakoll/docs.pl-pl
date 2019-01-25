---
title: ICorDebugManagedCallback::LoadClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c430e18864c0352b43641bce9a7d52af69cc80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718224"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="c26a6-102">ICorDebugManagedCallback::LoadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="c26a6-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="c26a6-103">Powiadamia debuger załadowano klasy.</span><span class="sxs-lookup"><span data-stu-id="c26a6-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c26a6-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c26a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c26a6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c26a6-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do którego został załadowany w klasie.</span><span class="sxs-lookup"><span data-stu-id="c26a6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="c26a6-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="c26a6-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26a6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c26a6-108">Remarks</span></span>  
 <span data-ttu-id="c26a6-109">To wywołanie zwrotne występuje tylko wtedy, gdy podczas ładowania klasy został włączony dla modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="c26a6-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="c26a6-110">Podczas ładowania klasy jest zawsze włączone dla modułów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c26a6-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="c26a6-111">`LoadClass` Wywołanie zwrotne odpowiedni moment, aby powiązać punkty przerwania z nowo wygenerowane klasy modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="c26a6-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26a6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c26a6-112">Requirements</span></span>  
 <span data-ttu-id="c26a6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26a6-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c26a6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c26a6-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c26a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c26a6-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26a6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c26a6-117">See also</span></span>
- [<span data-ttu-id="c26a6-118">UnloadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="c26a6-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="c26a6-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c26a6-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
