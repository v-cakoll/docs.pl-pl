---
title: ICorDebugModule::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97cecd66462cf6a88012b13dec82dbf617891dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493846"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="c111d-102">ICorDebugModule::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="c111d-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="c111d-103">Pobiera proces zawierający ten moduł.</span><span class="sxs-lookup"><span data-stu-id="c111d-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c111d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c111d-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c111d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c111d-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="c111d-106">[out] Wskaźnik na adres obiektu ICorDebugProcess, który reprezentuje proces zawierający ten moduł.</span><span class="sxs-lookup"><span data-stu-id="c111d-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c111d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c111d-107">Requirements</span></span>  
 <span data-ttu-id="c111d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c111d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c111d-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c111d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c111d-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c111d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c111d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c111d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
