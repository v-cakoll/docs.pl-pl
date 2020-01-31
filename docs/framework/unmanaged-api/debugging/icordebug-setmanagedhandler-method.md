---
title: ICorDebug::SetManagedHandler — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788970"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="8f178-102">ICorDebug::SetManagedHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f178-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="8f178-103">Określa obiekt obsługi zdarzeń dla zdarzeń zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8f178-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f178-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f178-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f178-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f178-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="8f178-106">podczas Wskaźnik do obiektu [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , który jest obiektem procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f178-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f178-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f178-107">Remarks</span></span>  
 <span data-ttu-id="8f178-108">`SetManagedHandler` musi być wywoływana w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8f178-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="8f178-109">Jeśli implementacja `ICorDebugManagedCallback` nie zawiera wystarczających interfejsów do obsługi zdarzeń debugowania dla debugowanej aplikacji, `SetManagedHandler` zwraca wynik HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="8f178-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f178-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f178-110">Requirements</span></span>  
 <span data-ttu-id="8f178-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f178-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f178-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f178-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f178-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f178-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f178-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f178-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f178-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f178-115">See also</span></span>

- [<span data-ttu-id="8f178-116">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f178-116">ICorDebug Interface</span></span>](icordebug-interface.md)
