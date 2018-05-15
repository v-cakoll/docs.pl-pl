---
title: ICorDebugVariableSymbol::GetName — metoda
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73aa5a9ca6625ab58e451449fab4c98f8b83014e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="f39ae-102">ICorDebugVariableSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="f39ae-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="f39ae-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f39ae-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f39ae-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f39ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f39ae-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f39ae-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="f39ae-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f39ae-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="f39ae-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f39ae-108">Wskaźnik do tablicy znaków, która zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f39ae-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f39ae-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f39ae-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f39ae-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f39ae-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f39ae-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f39ae-111">Requirements</span></span>  
 <span data-ttu-id="f39ae-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f39ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f39ae-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f39ae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f39ae-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f39ae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f39ae-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f39ae-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39ae-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f39ae-116">See Also</span></span>  
 [<span data-ttu-id="f39ae-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f39ae-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="f39ae-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f39ae-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
