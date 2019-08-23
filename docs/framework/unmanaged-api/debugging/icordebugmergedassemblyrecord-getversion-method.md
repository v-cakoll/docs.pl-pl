---
title: 'ICorDebugMergedAssemblyRecord:: GetVersion — Metoda'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9133ab1b7d3985d3a383bb36dcbea315548c00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939927"
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
 Informacje o numerach wersji zestawu znajdują się <xref:System.Version> w temacie dotyczącym klas.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
