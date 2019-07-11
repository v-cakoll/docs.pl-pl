---
title: Metoda ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb7861e33a02b994c4c29569a811f4e2f3c44cec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762310"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Metoda ICorDebugMergedAssemblyRecord::GetVersion
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
 [out] Wskaźnik do główny numer wersji.  
  
 `pMinor`  
 [out] Wskaźnik do pomocniczy numer wersji.  
  
 `pBuild`  
 [out] Wskaźnik do numeru kompilacji.  
  
 `pRevision`  
 [out] Wskaźnik do numer poprawki.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacji o numerach wersji zestawu, zobacz <xref:System.Version> temat poświęcony klasie.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
