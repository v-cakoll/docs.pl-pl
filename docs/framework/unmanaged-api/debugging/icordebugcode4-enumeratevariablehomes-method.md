---
title: "ICorDebugCode4::EnumerateVariableHomes — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4.EnumerateVariableHomes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4623f4bb1af21d19446b4e0f65dd5d826c412ccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="32646-102">ICorDebugCode4::EnumerateVariableHomes — metoda</span><span class="sxs-lookup"><span data-stu-id="32646-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="32646-103">Pobiera moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="32646-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32646-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32646-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32646-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32646-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="32646-106">Wskaźnik do adresu [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiektu interfejsu, który moduł wyliczający dla zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="32646-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32646-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32646-107">Remarks</span></span>  
 <span data-ttu-id="32646-108">[ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiekt interfejsu jest standardowy moduł pochodzące z interfejsu "ICorDebugEnum", która umożliwia wyliczyć [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="32646-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="32646-109">Kolekcja może zawierać wielu [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów dla tego samego miejsca lub argumentu indeksu, jeśli mają inną domach w różnych punktach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="32646-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32646-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32646-110">Requirements</span></span>  
 <span data-ttu-id="32646-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32646-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32646-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32646-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32646-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32646-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32646-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32646-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32646-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32646-115">See Also</span></span>  
 [<span data-ttu-id="32646-116">Interfejs ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="32646-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [<span data-ttu-id="32646-117">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="32646-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
