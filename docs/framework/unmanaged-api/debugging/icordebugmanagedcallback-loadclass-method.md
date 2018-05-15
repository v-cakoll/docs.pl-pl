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
ms.openlocfilehash: f1d920a97338bba3e90ec8f0c440f6dd2a93e722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="feaae-102">ICorDebugManagedCallback::LoadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="feaae-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="feaae-103">Powiadamia debuger załadowaniu klasy.</span><span class="sxs-lookup"><span data-stu-id="feaae-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feaae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="feaae-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="feaae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="feaae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="feaae-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, do którego został załadowany w klasie.</span><span class="sxs-lookup"><span data-stu-id="feaae-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="feaae-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="feaae-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feaae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="feaae-108">Remarks</span></span>  
 <span data-ttu-id="feaae-109">To wywołanie zwrotne występuje tylko wtedy, gdy podczas ładowania klasy została włączona dla modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="feaae-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="feaae-110">Podczas ładowania klasy jest zawsze włączona dla modułów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="feaae-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="feaae-111">`LoadClass` Wywołania zwrotnego zapewnia odpowiedni czas powiązać punktów przerwania z nowo wygenerowane klasy dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="feaae-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feaae-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="feaae-112">Requirements</span></span>  
 <span data-ttu-id="feaae-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feaae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feaae-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="feaae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="feaae-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feaae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feaae-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feaae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feaae-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="feaae-117">See Also</span></span>  
 [<span data-ttu-id="feaae-118">UnloadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="feaae-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="feaae-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="feaae-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
