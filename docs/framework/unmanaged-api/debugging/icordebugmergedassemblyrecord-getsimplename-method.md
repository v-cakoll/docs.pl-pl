---
title: ICorDebugMergedAssemblyRecord::Metoda GetSimpleName
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178706"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetSimpleName
Pobiera prostą nazwę zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [w] Liczba znaków w `szName` buforze.  
  
 `pcchName`  
 [na zewnątrz] Wskaźnik do liczby znaków faktycznie zapisane `szName` w buforze.  
  
 `szName`  
 Wskaźnik do tablicy znaków.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera prostą nazwę zestawu (na przykład "System.Collections"), bez rozszerzenia pliku, wersji, kultury lub tokenu klucza publicznego. Odpowiada właściwości w <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> kodzie zarządzanym.  
  
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
