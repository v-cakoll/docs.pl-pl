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
ms.openlocfilehash: 6a4cadae7a43d0cd965e51535eae2c95e59900d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130016"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="186b3-102">ICorDebugVariableHome::GetCode Method</span><span class="sxs-lookup"><span data-stu-id="186b3-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="186b3-103">Pobiera wystąpienie "ICorDebugCode", który zawiera ten [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="186b3-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="186b3-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="186b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="186b3-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="186b3-106">[out] Wskaźnik na adres wystąpienia "ICorDebugCode", który zawiera ten [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="186b3-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="186b3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="186b3-107">Requirements</span></span>  
 <span data-ttu-id="186b3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="186b3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="186b3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="186b3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="186b3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="186b3-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="186b3-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="186b3-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="186b3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="186b3-112">See also</span></span>

- [<span data-ttu-id="186b3-113">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="186b3-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
