---
title: "ICorDebugEval2::CallParameterizedFunction — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 055ded7f3309ff1011d1ca390daf353cba870376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction — Metoda
Konfiguruje wywołanie do określonego ICorDebugFunction, które mogą być zagnieżdżone wewnątrz klasy, w których Konstruktor pobiera <xref:System.Type> parametrów lub mogą się zająć <xref:System.Type> parametrów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFunction`  
 [in] Wskaźnik do `ICorDebugFunction` obiekt, który reprezentuje funkcję, która ma zostać wywołana.  
  
 `nTypeArgs`  
 [in] Liczba argumentów, które funkcja przyjmuje.  
  
 `ppTypeArgs`  
 [in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argumentu funkcji.  
  
 `nArgs`  
 [in] Liczba wartości przekazanych w funkcji.  
  
 `ppArgs`  
 [in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość przekazano argument funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `CallParameterizedFunction`przypomina [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) z tą różnicą, że funkcja może być wewnątrz klasy z parametrami typu, może się zająć parametry typu lub obie. Argumenty typu należy najpierw dla klasy, a następnie dla funkcji.  
  
 Jeśli funkcja znajduje się w domenie innej aplikacji, nastąpi przejście. Jednak wszystkie argumenty typu i wartości muszą być w docelowej domenie aplikacji.  
  
 Obliczanie funkcji można wykonać tylko w scenariuszach ograniczone. Jeśli `CallParameterizedFunction` lub `ICorDebugEval::CallFunction` kończy się niepowodzeniem, HRESULT zwrócony wskaże najbardziej ogólnym możliwe przyczyny błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
