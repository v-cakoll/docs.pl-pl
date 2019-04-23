---
title: ICorDebugCode4::EnumerateVariableHomes Method
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e4f6e7e3107516476b179b0ed718ca44bb114
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103400"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="af078-102">ICorDebugCode4::EnumerateVariableHomes Method</span><span class="sxs-lookup"><span data-stu-id="af078-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="af078-103">Pobiera moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af078-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af078-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af078-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af078-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af078-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="af078-106">Wskaźnik na adres [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiektu interfejsu, który jest moduł wyliczający dla zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af078-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af078-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af078-107">Remarks</span></span>  
 <span data-ttu-id="af078-108">[ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) obiektu interfejsu jest standardowy moduł wyliczający, pochodzące z interfejsu "ICorDebugEnum", która pozwala na wyliczenie [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="af078-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="af078-109">Kolekcja może zawierać wiele [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów dla tego samego indeksu gniazdo lub argumentu, jeśli mają one różne domach w różnych punktach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af078-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af078-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af078-110">Requirements</span></span>  
 <span data-ttu-id="af078-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af078-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af078-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af078-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af078-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af078-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af078-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af078-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af078-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af078-115">See also</span></span>

- [<span data-ttu-id="af078-116">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="af078-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="af078-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="af078-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
