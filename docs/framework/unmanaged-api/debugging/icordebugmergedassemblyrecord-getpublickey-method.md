---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793118"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda
Pobiera klucz publiczny zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKey`  
 podczas Maksymalna liczba bajtów w tablicy `pbPublicKey`.  
  
 `pcbPublicKey`  
 określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do tablicy `pbPublicKey`.  
  
 `pbPublicKey`  
 określoną Wskaźnik do tablicy bajtów zawierającej klucz publiczny zestawu.  
  
## <a name="remarks"></a>Uwagi  
  
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
