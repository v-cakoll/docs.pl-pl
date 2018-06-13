---
title: ICorDebugMergedAssemblyRecord::GetVersion — metoda
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb206d1bf39307852dd317613eb81028b777514d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414602"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord::GetVersion — metoda
Pobiera informacje o wersji zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMajor`  
 [out] Wskaźnik do głównego numeru wersji.  
  
 `pMinor`  
 [out] Wskaźnik do podrzędny numer wersji.  
  
 `pBuild`  
 [out] Wskaźnik do numeru kompilacji.  
  
 `pRevision`  
 [out] Wskaźnik do numer wersji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje na numery wersji zestawu, zobacz <xref:System.Version> klasy tematu.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
