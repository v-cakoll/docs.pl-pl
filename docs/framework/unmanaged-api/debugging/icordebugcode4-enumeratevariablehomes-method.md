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
ms.openlocfilehash: 5f731b1459542c3f5378790b21f2ea576e89ad97
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893341"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="af442-102">ICorDebugCode4:: EnumerateVariableHomes, Metoda</span><span class="sxs-lookup"><span data-stu-id="af442-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="af442-103">Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af442-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af442-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af442-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af442-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af442-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="af442-106">Wskaźnik do adresu obiektu interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) , który jest modułem wyliczającym dla zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af442-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af442-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af442-107">Remarks</span></span>  
 <span data-ttu-id="af442-108">Obiekt interfejsu [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu "ICorDebugEnum", który umożliwia Wyliczenie obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af442-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="af442-109">Kolekcja może zawierać wiele obiektów [ICorDebugVariableHome](icordebugvariablehome-interface.md) dla tego samego miejsca lub indeksu argumentów, jeśli mają różne domy w różnych punktach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="af442-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af442-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af442-110">Requirements</span></span>  
 <span data-ttu-id="af442-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af442-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af442-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af442-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af442-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af442-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af442-114">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af442-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af442-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af442-115">See also</span></span>

- [<span data-ttu-id="af442-116">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="af442-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="af442-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="af442-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
