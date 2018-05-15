---
title: ICorDebugVariableHome::GetCode — metoda
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
ms.openlocfilehash: ee8fa8feebba7258fc84ee7ba00ce2ab1977faa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="8b5cf-102">ICorDebugVariableHome::GetCode — metoda</span><span class="sxs-lookup"><span data-stu-id="8b5cf-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="8b5cf-103">Pobiera wystąpienie "ICorDebugCode", który zawiera ten [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b5cf-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5cf-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b5cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b5cf-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="8b5cf-106">[out] Wskaźnik do wystąpienia "ICorDebugCode", który zawiera ten adres [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b5cf-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5cf-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5cf-107">Requirements</span></span>  
 <span data-ttu-id="8b5cf-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5cf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5cf-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b5cf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b5cf-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b5cf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b5cf-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5cf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5cf-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b5cf-112">See Also</span></span>  
 [<span data-ttu-id="8b5cf-113">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5cf-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 
