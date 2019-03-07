---
title: ICorDebugMergedAssemblyRecord::GetPublicKey Method
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb14cd3812a632970acec353e05cbd190cb40081
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497057"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKey Method
Pobiera klucz publiczny zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKey`  
 [in] Maksymalna liczba bajtów w `pbPublicKey` tablicy.  
  
 `pcbPublicKey`  
 [out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKey` tablicy.  
  
 `pbPublicKey`  
 [out] Wskaźnik do tablicy typu byte, który zawiera klucz publiczny zestawu.  
  
## <a name="remarks"></a>Uwagi  
  
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
