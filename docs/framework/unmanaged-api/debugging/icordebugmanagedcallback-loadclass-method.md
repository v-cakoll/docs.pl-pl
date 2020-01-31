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
ms.openlocfilehash: cc5a2e1de79d6ba04ff3bf2bf86e0cb7ce9a5c0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788387"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="d57e0-102">ICorDebugManagedCallback::LoadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="d57e0-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="d57e0-103">Powiadamia debuger o załadowaniu klasy.</span><span class="sxs-lookup"><span data-stu-id="d57e0-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d57e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d57e0-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d57e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d57e0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d57e0-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której Klasa została załadowana.</span><span class="sxs-lookup"><span data-stu-id="d57e0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="d57e0-107">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="d57e0-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d57e0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d57e0-108">Remarks</span></span>  
 <span data-ttu-id="d57e0-109">To wywołanie zwrotne występuje tylko wtedy, gdy dla modułu zawierającego klasę włączono funkcję ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="d57e0-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="d57e0-110">Ładowanie klasy jest zawsze włączone dla modułów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="d57e0-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="d57e0-111">Wywołanie zwrotne `LoadClass` zapewnia odpowiedni czas na powiązanie punktów przerwania z nowo wygenerowanymi klasami w modułach dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="d57e0-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d57e0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d57e0-112">Requirements</span></span>  
 <span data-ttu-id="d57e0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d57e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d57e0-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d57e0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d57e0-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d57e0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d57e0-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d57e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57e0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d57e0-117">See also</span></span>

- [<span data-ttu-id="d57e0-118">UnloadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="d57e0-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="d57e0-119">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d57e0-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
