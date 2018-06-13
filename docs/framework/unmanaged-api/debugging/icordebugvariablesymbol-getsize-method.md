---
title: ICorDebugVariableSymbol::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01349b6418008db51c432d5c49f8491a44ab60d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419413"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="86bee-102">ICorDebugVariableSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="86bee-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="86bee-103">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="86bee-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86bee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86bee-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86bee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86bee-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="86bee-106">Wskaźnik do 32-bitowa liczba całkowita bez znaku zawierający rozmiar zmiennej.</span><span class="sxs-lookup"><span data-stu-id="86bee-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86bee-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86bee-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86bee-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="86bee-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86bee-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86bee-109">Requirements</span></span>  
 <span data-ttu-id="86bee-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86bee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86bee-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86bee-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86bee-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86bee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86bee-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86bee-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86bee-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86bee-114">See Also</span></span>  
 [<span data-ttu-id="86bee-115">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="86bee-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="86bee-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="86bee-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
