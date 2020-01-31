---
title: ICorDebugMergedAssemblyRecord, interfejs
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793068"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord, interfejs
Zawiera informacje o scalonym zestawie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCulture, metoda](icordebugmergedassemblyrecord-getculture-method.md)|Pobiera ciąg nazwy kultury zestawu.|  
|[GetIndex, metoda](icordebugmergedassemblyrecord-getindex-method.md)|Pobiera indeks prefiksu zestawu.|  
|[GetPublicKey, metoda](icordebugmergedassemblyrecord-getpublickey-method.md)|Pobiera klucz publiczny zestawu.|  
|[GetPublicKeyToken, metoda](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Pobiera token klucza publicznego zestawu.|  
|[GetSimpleName, metoda](icordebugmergedassemblyrecord-getsimplename-method.md)|Pobiera prostą nazwę zestawu.|  
|[GetVersion, metoda](icordebugmergedassemblyrecord-getversion-method.md)|Pobiera informacje o wersji zestawu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
