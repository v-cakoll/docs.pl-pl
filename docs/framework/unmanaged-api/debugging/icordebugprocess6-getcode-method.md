---
title: Metoda ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572b279ddfdb1fb0eb9da4b0d1f8c2cb12c8a46b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="7bfda-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="7bfda-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="7bfda-103">Pobiera informacje o zarządzanego kodu pod adresem określonym kodem.</span><span class="sxs-lookup"><span data-stu-id="7bfda-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bfda-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bfda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bfda-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="7bfda-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która określa początkowy adres segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7bfda-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="7bfda-107">[out] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="7bfda-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bfda-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bfda-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bfda-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7bfda-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfda-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bfda-110">Requirements</span></span>  
 <span data-ttu-id="7bfda-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bfda-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfda-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bfda-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bfda-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bfda-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bfda-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfda-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfda-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bfda-115">See Also</span></span>  
 [<span data-ttu-id="7bfda-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bfda-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="7bfda-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7bfda-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
