---
title: 'ICorDebugMergedAssemblyRecord:: getsimplename — Metoda'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 565e27b47f2454dec1e4c2b89ee46ac5279b08b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130549"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord:: getsimplename — Metoda
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
 podczas Liczba znaków w buforze `szName`.  
  
 `pcchName`  
 określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.  
  
 `szName`  
 Wskaźnik do tablicy znaków.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera prostą nazwę zestawu (na przykład "System. Collections") bez rozszerzenia pliku, wersji, kultury lub tokenu klucza publicznego. Odpowiada właściwości <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> w kodzie zarządzanym.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
