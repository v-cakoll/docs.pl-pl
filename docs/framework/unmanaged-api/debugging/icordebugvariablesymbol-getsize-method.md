---
title: ICorDebugVariableSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e963e655c933c9191953bb32ba0b73adf0ae86d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774869"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="bdafe-102">ICorDebugVariableSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="bdafe-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="bdafe-103">Pobiera rozmiar zmiennej elementu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bdafe-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdafe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdafe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdafe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdafe-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="bdafe-106">Wskaźnik 32-bitowa liczba całkowita bez znaku zawierający rozmiar zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bdafe-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdafe-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdafe-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdafe-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdafe-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdafe-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdafe-109">Requirements</span></span>  
 <span data-ttu-id="bdafe-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdafe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdafe-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdafe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdafe-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdafe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdafe-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdafe-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdafe-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdafe-114">See also</span></span>

- [<span data-ttu-id="bdafe-115">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="bdafe-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="bdafe-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bdafe-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
