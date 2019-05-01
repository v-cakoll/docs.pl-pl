---
title: ICorDebugEval2::CallParameterizedFunction — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934840"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction — Metoda
Konfiguruje wywołanie do określonego ICorDebugFunction, które mogą być zagnieżdżone wewnątrz klasy, której Konstruktor przyjmuje <xref:System.Type> parametrów lub mogą się zająć <xref:System.Type> parametrów.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pFunction`  
 [in] Wskaźnik do `ICorDebugFunction` obiekt, który reprezentuje funkcja do wywołania.  
  
 `nTypeArgs`  
 [in] Liczba argumentów, które funkcja przyjmuje.  
  
 `ppTypeArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje argumentu funkcji.  
  
 `nArgs`  
 [in] Liczba wartości przekazywane w funkcji.  
  
 `ppArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, która reprezentuje wartość przekazanego argumentu funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `CallParameterizedFunction` przypomina [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) z tą różnicą, że funkcja może być wewnątrz klasy z parametrami typu, może się zająć parametrów typu i / lub. Argumenty typu powinien być podawany najpierw dla klasy, a następnie dla tej funkcji.  
  
 Jeśli funkcja znajduje się w domenie innej aplikacji, nastąpi przejście. Jednak wszystkie argumenty typu i wartości musi należeć do domeny aplikacji docelowej.  
  
 Obliczanie funkcji mogą być wykonywane tylko w ograniczonej liczbie scenariuszy. Jeśli `CallParameterizedFunction` lub `ICorDebugEval::CallFunction` zakończy się niepowodzeniem, zwrócona wartość HRESULT będą wskazywać najbardziej ogólną możliwe przyczyny błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
