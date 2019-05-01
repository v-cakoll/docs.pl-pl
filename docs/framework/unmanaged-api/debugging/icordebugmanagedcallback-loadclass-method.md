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
ms.openlocfilehash: 39ce3e8329c4ff32b55341127f68a800246677df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995218"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="5f803-102">ICorDebugManagedCallback::LoadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f803-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="5f803-103">Powiadamia debuger załadowano klasy.</span><span class="sxs-lookup"><span data-stu-id="5f803-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f803-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f803-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f803-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f803-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5f803-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do którego został załadowany w klasie.</span><span class="sxs-lookup"><span data-stu-id="5f803-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="5f803-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="5f803-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f803-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f803-108">Remarks</span></span>  
 <span data-ttu-id="5f803-109">To wywołanie zwrotne występuje tylko wtedy, gdy podczas ładowania klasy został włączony dla modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="5f803-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="5f803-110">Podczas ładowania klasy jest zawsze włączone dla modułów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="5f803-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="5f803-111">`LoadClass` Wywołanie zwrotne odpowiedni moment, aby powiązać punkty przerwania z nowo wygenerowane klasy modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="5f803-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f803-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f803-112">Requirements</span></span>  
 <span data-ttu-id="5f803-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f803-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f803-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f803-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f803-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f803-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f803-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f803-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f803-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f803-117">See also</span></span>

- [<span data-ttu-id="5f803-118">UnloadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="5f803-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="5f803-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f803-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
