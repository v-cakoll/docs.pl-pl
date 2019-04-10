---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206086"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>Metoda ICorDebugAssembly3::GetContainerAssembly
Zwraca zestaw kontenerów to `ICorDebugAssembly3` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssembly`  
 Wskaźnik na adres ICorDebugAssembly obiekt, który reprezentuje zestaw kontenerów lub **null** Jeśli wywołanie metody nie powiedzie się.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli wywołanie metody zakończy się pomyślnie; w przeciwnym razie `S_FALSE`, i `ppAssembly` jest **null**.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten zestaw został połączony z innymi osobami w zestawu pojedynczego kontenera, ta metoda zwraca zestaw kontenerów. Aby uzyskać więcej informacji i terminologii, zobacz [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tematu.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejs ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
