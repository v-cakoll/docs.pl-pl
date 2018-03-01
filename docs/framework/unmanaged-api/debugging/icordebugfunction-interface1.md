---
title: ICorDebugFunction Interface1
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
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
Reprezentuje zarządzaną funkcję lub metodę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Tworzy punkt przerwania na początku tej funkcji.|  
|[GetClass, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Pobiera obiekt ICorDebugClass, który reprezentuje klasę, którą ta funkcja jest elementem członkowskim.|  
|[GetCurrentVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Pobiera numer wersji najnowszej edycji wykonanych dla tej funkcji.|  
|[GetILCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Pobiera kod języka pośredniego (MSIL) firmy Microsoft dla tej funkcji.|  
|[GetLocalVarSigToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Pobiera metadane token do lokalnej zmiennej podpisu funkcji, która jest reprezentowana przez to `ICorDebugFunction` wystąpienia.|  
|[GetModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Pobiera moduł, w którym ta funkcja jest zdefiniowany.|  
|[GetNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Pobiera kod natywny dla tej funkcji.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Pobiera token metadanych dla tej funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugFunction` Interfejsu nie reprezentuje funkcję z parametrami typu ogólnego. Na przykład `ICorDebugFunction` reprezentuje wystąpienie `Func<T>` , ale nie `Func<string>`. Wywołanie [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) można pobrać parametrów typu ogólnego.  
  
 Relacja między token metadanych metody, `mdMethodDef`, a także metodę `ICorDebugFunction` obiektu jest zależne od tego, czy Edytuj i Kontynuuj jest dozwolony w funkcji:  
  
-   Jeśli Edytuj i Kontynuuj jest niedozwolone w funkcji i jeden do jednego relację między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu. Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden `mdMethodDef` tokenu.  
  
-   Jeśli Edytuj i Kontynuuj jest dozwolony w funkcji, istnieje relacja wiele do jednego między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu. Oznacza to, że funkcja może mieć wielu wystąpień `ICorDebugFunction`, jeden dla każdej wersji, funkcji, ale tylko jeden `mdMethodDef` tokenu.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
