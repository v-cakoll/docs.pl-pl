---
title: ICorDebugEval::NewObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff378602fc7338263ef49aee6802d2138bab9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413175"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject — Metoda
Przydziela nowe wystąpienie obiektu i wywołuje metodę określony Konstruktor.  
  
 Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0. Użyj [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pConstructor`  
 [in] Konstruktor, który ma zostać wywołana.  
  
 `nArgs`  
 [in] Rozmiar `ppArgs` tablicy.  
  
 `ppArgs`  
 [in] Tablica obiektów ICorDebugValue, z których każdy reprezentuje argument przekazywany do konstruktora.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [NewParameterizedObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
