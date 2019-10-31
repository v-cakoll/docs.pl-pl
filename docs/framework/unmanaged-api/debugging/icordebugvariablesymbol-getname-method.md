---
title: 'ICorDebugVariableSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121012"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="da56b-102">ICorDebugVariableSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="da56b-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="da56b-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="da56b-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da56b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da56b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da56b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da56b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="da56b-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="da56b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="da56b-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="da56b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="da56b-108">Wskaźnik do tablicy znaków, która zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="da56b-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da56b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da56b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da56b-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da56b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da56b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da56b-111">Requirements</span></span>  
 <span data-ttu-id="da56b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da56b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da56b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da56b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da56b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da56b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da56b-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da56b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da56b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da56b-116">See also</span></span>

- [<span data-ttu-id="da56b-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="da56b-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="da56b-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="da56b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
