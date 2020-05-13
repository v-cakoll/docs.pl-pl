---
title: ICorDebugModule::GetAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: 86e2b28448caf2a872e44490e8ee4763b056ed44
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206967"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="cc422-102">ICorDebugModule::GetAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc422-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="cc422-103">Pobiera zawierający go zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="cc422-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc422-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc422-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc422-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc422-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="cc422-106">określoną Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw zawierający ten moduł.</span><span class="sxs-lookup"><span data-stu-id="cc422-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc422-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc422-107">Requirements</span></span>  
 <span data-ttu-id="cc422-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc422-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc422-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc422-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc422-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc422-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc422-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc422-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
