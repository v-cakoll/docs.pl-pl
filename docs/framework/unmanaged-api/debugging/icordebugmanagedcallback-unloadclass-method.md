---
title: ICorDebugManagedCallback::UnloadClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: f2f19987d22502acbe06bd5e5c14b0d6c17cbe24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781585"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="d454a-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="d454a-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="d454a-103">Powiadamia debuger, że Klasa jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="d454a-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d454a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d454a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d454a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d454a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d454a-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą klasę.</span><span class="sxs-lookup"><span data-stu-id="d454a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="d454a-107">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="d454a-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d454a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d454a-108">Remarks</span></span>  
 <span data-ttu-id="d454a-109">Nie należy odwoływać się do klasy po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="d454a-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d454a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d454a-110">Requirements</span></span>  
 <span data-ttu-id="d454a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d454a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d454a-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d454a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d454a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d454a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d454a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d454a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d454a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d454a-115">See also</span></span>

- [<span data-ttu-id="d454a-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="d454a-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="d454a-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d454a-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
