---
title: ICorDebugArrayValue::GetElement — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088489"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement — Metoda
Pobiera wartość danego elementu tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cdim`  
 podczas Liczba wymiarów tego obiektu `ICorDebugArrayValue`.  
  
 Ta wartość jest również rozmiarem tablicy `indices`, ponieważ jej rozmiar jest równy liczbie wymiarów obiektu `ICorDebugArrayValue`.  
  
 `indices`  
 podczas Tablica wartości indeksu, z których każdy określa pozycję w wymiarze obiektu `ICorDebugArrayValue`.  
  
 Ta wartość nie może być równa null.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość określonego elementu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
