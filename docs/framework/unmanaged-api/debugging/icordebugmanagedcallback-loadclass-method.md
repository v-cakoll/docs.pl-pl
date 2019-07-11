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
ms.openlocfilehash: 5619dea17b9a7140238fd559d2f6b1a5d190ac33
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761897"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="c2448-102">ICorDebugManagedCallback::LoadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2448-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="c2448-103">Powiadamia debuger załadowano klasy.</span><span class="sxs-lookup"><span data-stu-id="c2448-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2448-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2448-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2448-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2448-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c2448-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do którego został załadowany w klasie.</span><span class="sxs-lookup"><span data-stu-id="c2448-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="c2448-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="c2448-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2448-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2448-108">Remarks</span></span>  
 <span data-ttu-id="c2448-109">To wywołanie zwrotne występuje tylko wtedy, gdy podczas ładowania klasy został włączony dla modułu, który zawiera klasę.</span><span class="sxs-lookup"><span data-stu-id="c2448-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="c2448-110">Podczas ładowania klasy jest zawsze włączone dla modułów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c2448-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="c2448-111">`LoadClass` Wywołanie zwrotne odpowiedni moment, aby powiązać punkty przerwania z nowo wygenerowane klasy modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="c2448-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2448-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2448-112">Requirements</span></span>  
 <span data-ttu-id="c2448-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2448-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2448-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2448-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2448-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2448-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2448-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2448-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2448-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2448-117">See also</span></span>

- [<span data-ttu-id="c2448-118">UnloadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="c2448-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="c2448-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c2448-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
