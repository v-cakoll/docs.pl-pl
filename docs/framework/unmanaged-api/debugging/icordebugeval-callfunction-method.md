---
title: ICorDebugEval::CallFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589402"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction — Metoda
Konfiguruje wywołanie do określonej funkcji.  
  
 Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.  
  
 `nArgs`  
 [in] Liczba argumentów funkcji.  
  
 `ppArgs`  
 [in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, który określa argument, który zostanie przekazany do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja znajduje się wirtualny, `CallFunction` wykona wirtualnego wysyłania. Jeśli funkcja znajduje się w domenie innej aplikacji, przejście wystąpi tak długo, jak wszystkie argumenty mają również w tej domenie aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** WindowSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz także
- [CallParameterizedFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
