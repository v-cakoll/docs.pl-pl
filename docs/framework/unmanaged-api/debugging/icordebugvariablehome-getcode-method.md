---
title: ICorDebugVariableHome::GetCode Method
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216779ab03b426ceb8003accfbdd182f583b77cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557347"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="6c2ed-102">ICorDebugVariableHome::GetCode Method</span><span class="sxs-lookup"><span data-stu-id="6c2ed-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="6c2ed-103">Pobiera wystąpienie "ICorDebugCode", który zawiera ten [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="6c2ed-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c2ed-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c2ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c2ed-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="6c2ed-106">[out] Wskaźnik na adres wystąpienia "ICorDebugCode", który zawiera ten [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="6c2ed-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2ed-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c2ed-107">Requirements</span></span>  
 <span data-ttu-id="6c2ed-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c2ed-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2ed-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c2ed-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c2ed-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c2ed-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c2ed-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2ed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2ed-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c2ed-112">See also</span></span>
- [<span data-ttu-id="6c2ed-113">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c2ed-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

