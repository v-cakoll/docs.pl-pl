---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 95ed1303b33b328d1f14ecea6cc318e14991cd54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129787"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda
Pobiera token klucza publicznego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKeyToken`  
 podczas Maksymalna liczba bajtów w tablicy `pbPublicKeyToken`.  
  
 `pcbPublicKeyToken`  
 określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do tablicy `pbPublicKeyToken`.  
  
 `pbPublicKeyToken`  
 określoną Wskaźnik do tablicy bajtów zawierającej token klucza publicznego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Token klucza publicznego zestawu to ostatnie osiem bajtów skrótu SHA1 klucza publicznego.  
  
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
