---
title: 'ICorDebugVariableSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23637055e493c008db36b23515001895450d6ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967900"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="abd9a-102">ICorDebugVariableSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="abd9a-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="abd9a-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="abd9a-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abd9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abd9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abd9a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="abd9a-106">podczas Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="abd9a-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="abd9a-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="abd9a-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="abd9a-108">Wskaźnik do tablicy znaków, która zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="abd9a-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abd9a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abd9a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abd9a-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="abd9a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd9a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abd9a-111">Requirements</span></span>  
 <span data-ttu-id="abd9a-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd9a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd9a-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abd9a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abd9a-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abd9a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abd9a-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd9a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd9a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abd9a-116">See also</span></span>

- [<span data-ttu-id="abd9a-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="abd9a-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="abd9a-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="abd9a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
