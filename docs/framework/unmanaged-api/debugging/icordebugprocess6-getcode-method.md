---
title: Metoda ICorDebugProcess6::GetCode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f532c52ac487915b76d624e62886a93db6d1eae4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="daaa4-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="daaa4-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="daaa4-103">Pobiera informacje o zarządzanego kodu pod adresem określonym kodem.</span><span class="sxs-lookup"><span data-stu-id="daaa4-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daaa4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="daaa4-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="daaa4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="daaa4-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="daaa4-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która określa początkowy adres segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="daaa4-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="daaa4-107">[out] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="daaa4-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daaa4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daaa4-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daaa4-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="daaa4-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daaa4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daaa4-110">Requirements</span></span>  
 <span data-ttu-id="daaa4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daaa4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daaa4-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daaa4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daaa4-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daaa4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daaa4-114">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daaa4-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daaa4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daaa4-115">See Also</span></span>  
 [<span data-ttu-id="daaa4-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="daaa4-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="daaa4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="daaa4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
