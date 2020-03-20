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
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179008"
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
 [w] Liczba wymiarów tego `ICorDebugArrayValue` obiektu.  
  
 Ta wartość jest również `indices` rozmiar tablicy, ponieważ jej rozmiar jest `ICorDebugArrayValue` równy liczbie wymiarów obiektu.  
  
 `indices`  
 [w] Tablica wartości indeksu, z których każda określa pozycję `ICorDebugArrayValue` w wymiarze obiektu.  
  
 Ta wartość nie może być null.  
  
 `ppValue`  
 [na zewnątrz] Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość określonego elementu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
