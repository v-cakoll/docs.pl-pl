---
title: ICorDebugHeapValue2::CreateHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178878"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle — Metoda
Tworzy dojście określonego typu dla wartości sterty reprezentowanej przez ten obiekt ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 [w] Wartość wyliczenia CorDebugHandleType, która określa typ dojścia do utworzenia.  
  
 `ppHandle`  
 [na zewnątrz] Wskaźnik do adresu obiektu ICorDebugHandleValue, który reprezentuje nowy dojście dla tej wartości sterty.  
  
## <a name="remarks"></a>Uwagi  
 Dojście zostanie utworzony w domenie aplikacji, która jest skojarzona z wartością sterty i stanie się nieprawidłowa, jeśli domena aplikacji zostanie zwolniona.  
  
 Wiele wywołań tej funkcji dla tej samej wartości sterty utworzy wiele uchwytów. Ponieważ uchwyty wpływają na wydajność modułu zbierającego elementy bezużyteczne, debuger powinien ograniczyć się do stosunkowo niewielkiej liczby uchwytów (około 256), które są aktywne w czasie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
