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
ms.openlocfilehash: ab31ab8f83a71372c8e12b460458a26996f65ff5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782988"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction — Metoda
Konfiguruje wywołanie do określonego ICorDebugFunction, które może być zagnieżdżone wewnątrz klasy, której Konstruktor przyjmuje <xref:System.Type> parametry, lub sama może przyjmować <xref:System.Type> parametry.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Wskaźnik do obiektu `ICorDebugFunction`, który reprezentuje funkcję, która ma zostać wywołana.  
  
 `nTypeArgs`  
 podczas Liczba argumentów, które wykonuje funkcja.  
  
 `ppTypeArgs`  
 podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argument funkcji.  
  
 `nArgs`  
 podczas Liczba wartości przekazaną w funkcji.  
  
 `ppArgs`  
 podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość przekazaną w argumencie funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `CallParameterizedFunction` przypomina [ICorDebugEval:: CallFunction —](icordebugeval-callfunction-method.md) , z tą różnicą, że funkcja może znajdować się wewnątrz klasy z parametrami typu, może same przyjmować parametry typu lub oba te metody. Argumenty typu powinny być określone jako pierwsze dla klasy, a następnie dla funkcji.  
  
 Jeśli funkcja znajduje się w innej domenie aplikacji, nastąpi przejście. Jednak wszystkie argumenty typu i wartości muszą znajdować się w domenie aplikacji docelowej.  
  
 Obliczanie funkcji można wykonać tylko w ograniczonych scenariuszach. Jeśli `CallParameterizedFunction` lub `ICorDebugEval::CallFunction` nie powiedzie się, zwrócony wynik HRESULT będzie wskazywał największą możliwą przyczynę niepowodzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
