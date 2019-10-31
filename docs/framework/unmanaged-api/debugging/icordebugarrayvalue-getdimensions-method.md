---
title: ICorDebugArrayValue::GetDimensions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: c5199794098e4d83588728eeb165aee5f81fe4c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088499"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a>ICorDebugArrayValue::GetDimensions — Metoda
Pobiera liczbę elementów w każdym wymiarze tej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cdim`  
 podczas Liczba wymiarów tego obiektu ICorDebugArrayValue.  
  
 Ta wartość jest również rozmiarem tablicy `dims`, ponieważ jej rozmiar jest równy liczbie wymiarów obiektu `ICorDebugArrayValue`.  
  
 `dims`  
 określoną Tablica liczb całkowitych, z których każdy określa liczbę elementów w wymiarze w tym obiekcie `ICorDebugArrayValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
