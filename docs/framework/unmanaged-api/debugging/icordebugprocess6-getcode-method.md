---
title: Metoda ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 810590f0d1f7f74b778d73d98a9f7f9b1988b75f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736440"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="2984c-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="2984c-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="2984c-103">Pobiera informacje o kodzie zarządzanym pod adresem określonym kodem.</span><span class="sxs-lookup"><span data-stu-id="2984c-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2984c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2984c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2984c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2984c-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="2984c-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która określa adres początkowy segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2984c-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="2984c-107">[out] Wskaźnik na adres obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2984c-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2984c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2984c-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2984c-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2984c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2984c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2984c-110">Requirements</span></span>  
 <span data-ttu-id="2984c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2984c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2984c-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2984c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2984c-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2984c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2984c-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2984c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2984c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2984c-115">See also</span></span>

- [<span data-ttu-id="2984c-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="2984c-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="2984c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2984c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
