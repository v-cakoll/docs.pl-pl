---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion — Metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 8b5995183be7f1c992cf3230e16456cb248eff0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793082"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord:: GetVersion — Metoda
Pobiera informacje o wersji zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMajor`  
 określoną Wskaźnik do głównego numeru wersji.  
  
 `pMinor`  
 określoną Wskaźnik do pomocniczego numeru wersji.  
  
 `pBuild`  
 określoną Wskaźnik do numeru kompilacji.  
  
 `pRevision`  
 określoną Wskaźnik do numeru poprawki.  
  
## <a name="remarks"></a>Uwagi  
 Informacje o numerach wersji zestawu znajdują się w temacie <xref:System.Version> Class.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
