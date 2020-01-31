---
title: ICorDebugManagedCallback::ControlCTrap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 63f7bf8c09480b9ce2cfb8eb8dc66e4a6133ef8f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777486"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="81cd2-102">ICorDebugManagedCallback::ControlCTrap — Metoda</span><span class="sxs-lookup"><span data-stu-id="81cd2-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="81cd2-103">Powiadamia debuger, że w debugowanym procesie jest zalewkowany skrót CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="81cd2-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81cd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81cd2-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81cd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81cd2-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="81cd2-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, w którym jest zalewkowany CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="81cd2-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81cd2-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="81cd2-107">Return Value</span></span>  
  
|<span data-ttu-id="81cd2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81cd2-108">HRESULT</span></span>|<span data-ttu-id="81cd2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="81cd2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81cd2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81cd2-110">S_OK</span></span>|<span data-ttu-id="81cd2-111">Debuger będzie obsługiwał pułapkę CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="81cd2-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="81cd2-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="81cd2-112">S_FALSE</span></span>|<span data-ttu-id="81cd2-113">Debuger nie będzie obsługiwał pułapki CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="81cd2-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81cd2-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81cd2-114">Remarks</span></span>  
 <span data-ttu-id="81cd2-115">Wszystkie domeny aplikacji w ramach procesu są zatrzymane dla tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="81cd2-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81cd2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81cd2-116">Requirements</span></span>  
 <span data-ttu-id="81cd2-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81cd2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81cd2-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81cd2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81cd2-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81cd2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81cd2-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81cd2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81cd2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81cd2-121">See also</span></span>

- [<span data-ttu-id="81cd2-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="81cd2-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
