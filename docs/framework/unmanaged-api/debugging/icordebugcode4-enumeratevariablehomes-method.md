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
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784088"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="97e3f-102">ICorDebugCode4:: EnumerateVariableHomes, Metoda</span><span class="sxs-lookup"><span data-stu-id="97e3f-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="97e3f-103">Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="97e3f-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97e3f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97e3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97e3f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="97e3f-106">Wskaźnik do adresu obiektu interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , który jest modułem wyliczającym dla zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="97e3f-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97e3f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97e3f-107">Remarks</span></span>  
 <span data-ttu-id="97e3f-108">Obiekt interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu "ICorDebugEnum", który umożliwia Wyliczenie obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="97e3f-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="97e3f-109">Kolekcja może zawierać wiele obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) dla tego samego miejsca lub indeksu argumentów, jeśli mają różne domy w różnych punktach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="97e3f-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e3f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97e3f-110">Requirements</span></span>  
 <span data-ttu-id="97e3f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e3f-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97e3f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97e3f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97e3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e3f-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e3f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97e3f-115">See also</span></span>

- [<span data-ttu-id="97e3f-116">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="97e3f-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="97e3f-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97e3f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
