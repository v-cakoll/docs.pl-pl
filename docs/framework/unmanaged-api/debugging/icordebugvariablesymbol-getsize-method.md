---
title: "ICorDebugVariableSymbol::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="2c6ad-102">ICorDebugVariableSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="2c6ad-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="2c6ad-103">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2c6ad-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c6ad-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c6ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c6ad-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="2c6ad-106">Wskaźnik do 32-bitowa liczba całkowita bez znaku zawierający rozmiar zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2c6ad-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c6ad-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c6ad-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c6ad-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2c6ad-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c6ad-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c6ad-109">Requirements</span></span>  
 <span data-ttu-id="2c6ad-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c6ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c6ad-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c6ad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c6ad-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c6ad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c6ad-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c6ad-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6ad-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c6ad-114">See Also</span></span>  
 [<span data-ttu-id="2c6ad-115">Interfejs ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="2c6ad-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="2c6ad-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="2c6ad-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
