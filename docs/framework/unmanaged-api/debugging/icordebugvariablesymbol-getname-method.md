---
title: "ICorDebugVariableSymbol::GetName — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 747249c23089cbeba04c3a872823f01f2b334203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="071a9-102">ICorDebugVariableSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="071a9-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="071a9-103">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="071a9-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="071a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="071a9-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="071a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="071a9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="071a9-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="071a9-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="071a9-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="071a9-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="071a9-108">Wskaźnik do tablicy znaków, która zawiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="071a9-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="071a9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="071a9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="071a9-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="071a9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="071a9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="071a9-111">Requirements</span></span>  
 <span data-ttu-id="071a9-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="071a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="071a9-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="071a9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="071a9-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="071a9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="071a9-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="071a9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071a9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="071a9-116">See Also</span></span>  
 [<span data-ttu-id="071a9-117">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="071a9-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="071a9-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="071a9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
