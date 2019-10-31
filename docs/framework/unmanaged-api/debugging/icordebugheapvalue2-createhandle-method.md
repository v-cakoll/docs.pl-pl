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
ms.openlocfilehash: b9eab1274f2d0ad562c0dec6adeddb85c6cfc458
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138391"
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
 podczas Wartość wyliczenia CorDebugHandleType —, która określa typ dojścia do utworzenia.  
  
 `ppHandle`  
 określoną Wskaźnik do adresu obiektu ICorDebugHandleValue, który reprezentuje nowe dojście dla tej wartości sterty.  
  
## <a name="remarks"></a>Uwagi  
 Dojście zostanie utworzone w domenie aplikacji skojarzonej z wartością sterty i stanie się nieprawidłowe, jeśli domena aplikacji zostanie zwolniona z ładowania.  
  
 Wielokrotne wywołania tej funkcji dla tej samej wartości sterty spowodują utworzenie wielu dojść. Ponieważ uchwyty wpływają na wydajność modułu wyrzucania elementów bezużytecznych, debuger powinien ograniczyć się do stosunkowo niewielkiej liczby dojść (około 256), które są aktywne w danym momencie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
