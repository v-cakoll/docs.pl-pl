---
title: ICorDebugMergedAssemblyRecord::Metoda GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178683"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetVersion
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
 [na zewnątrz] Wskaźnik do głównego numeru wersji.  
  
 `pMinor`  
 [na zewnątrz] Wskaźnik do pomocniczego numeru wersji.  
  
 `pBuild`  
 [na zewnątrz] Wskaźnik do numeru kompilacji.  
  
 `pRevision`  
 [na zewnątrz] Wskaźnik do numeru poprawki.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje na temat <xref:System.Version> numerów wersji zestawu, zobacz temat klasy.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
