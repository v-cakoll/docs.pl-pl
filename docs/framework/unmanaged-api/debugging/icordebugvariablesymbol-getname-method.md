---
title: Metoda ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b414e1fa035a50cdcfd317592f69abdc40fb0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684118"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="5fcc8-102">Metoda ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="5fcc8-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="5fcc8-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5fcc8-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fcc8-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fcc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fcc8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5fcc8-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5fcc8-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5fcc8-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5fcc8-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5fcc8-108">Wskaźnik do tablicy znaków, który zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5fcc8-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcc8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fcc8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fcc8-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5fcc8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcc8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fcc8-111">Requirements</span></span>  
 <span data-ttu-id="5fcc8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fcc8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcc8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fcc8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fcc8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fcc8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fcc8-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcc8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcc8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fcc8-116">See also</span></span>
- [<span data-ttu-id="5fcc8-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="5fcc8-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="5fcc8-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5fcc8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
