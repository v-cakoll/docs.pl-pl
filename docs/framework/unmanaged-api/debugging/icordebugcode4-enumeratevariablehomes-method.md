---
title: 'ICorDebugCode4:: EnumerateVariableHomes, Metoda'
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
ms.openlocfilehash: 850cbd2367dddd9f46375817e271cb8e7183cf64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121088"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="19278-102">ICorDebugCode4:: EnumerateVariableHomes, Metoda</span><span class="sxs-lookup"><span data-stu-id="19278-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="19278-103">Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="19278-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19278-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19278-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19278-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19278-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="19278-106">Wskaźnik do adresu obiektu interfejsu [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) , który jest modułem wyliczającym dla zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="19278-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19278-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19278-107">Remarks</span></span>  
 <span data-ttu-id="19278-108">Obiekt interfejsu [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu "ICorDebugEnum", który umożliwia Wyliczenie obiektów [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="19278-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="19278-109">Kolekcja może zawierać wiele obiektów [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) dla tego samego miejsca lub indeksu argumentów, jeśli mają różne domy w różnych punktach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="19278-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19278-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19278-110">Requirements</span></span>  
 <span data-ttu-id="19278-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19278-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19278-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19278-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19278-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19278-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19278-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19278-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19278-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19278-115">See also</span></span>

- [<span data-ttu-id="19278-116">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="19278-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="19278-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="19278-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
