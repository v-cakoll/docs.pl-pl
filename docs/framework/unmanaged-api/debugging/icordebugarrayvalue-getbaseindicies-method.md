---
title: ICorDebugArrayValue::GetBaseIndicies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: e103401b85626e53db53e1894c22b161774e5163
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088688"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a>ICorDebugArrayValue::GetBaseIndicies — Metoda
Pobiera podstawowy indeks każdego wymiaru w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cdim`  
 podczas Liczba wymiarów tego obiektu `ICorDebugArrayValue`. Ta wartość jest również rozmiarem tablicy `indicies`, ponieważ jej rozmiar jest równy liczbie wymiarów obiektu `ICorDebugArrayValue`.  
  
 `indicies`  
 określoną Tablica liczb całkowitych, z których każdy jest indeksem podstawowym (czyli indeksem początkowym) wymiaru tego obiektu `ICorDebugArrayValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
