---
title: ICorDebugVariableSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211845"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="fbec7-102">ICorDebugVariableSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="fbec7-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="fbec7-103">Pobiera rozmiar zmiennej elementu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="fbec7-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbec7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbec7-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbec7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbec7-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="fbec7-106">Wskaźnik 32-bitowa liczba całkowita bez znaku zawierający rozmiar zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fbec7-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbec7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbec7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbec7-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fbec7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbec7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbec7-109">Requirements</span></span>  
 <span data-ttu-id="fbec7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbec7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbec7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbec7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbec7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbec7-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fbec7-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fbec7-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbec7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbec7-114">See also</span></span>

- [<span data-ttu-id="fbec7-115">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbec7-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="fbec7-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="fbec7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
