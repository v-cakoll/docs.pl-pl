---
title: ICorDebugDataTarget::ReadVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412194"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual — Metoda
Pobiera blok pamięci ciągłej, zaczynając od określonego adresu i zwraca go do dostarczonego buforu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres początkowy żądaną ilość pamięci.  
  
 `pbuffer`  
 [out] Bufor, w którym będzie przechowywany pamięci.  
  
 `bytesRequested`  
 [in] Liczba bajtów do pobrania z adresu docelowego.  
  
 `pBytesRead`  
 [out] Liczba bajtów odczytanych w rzeczywistości z adresu docelowego. Może to być krótsza niż `bytesRequested`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pierwszy bajt (pod adresem określonym start) mogą być odczytywane; wywołanie powinien zwrócić Powodzenie (do obsługi wydajne odczytu struktur danych z samoopisujące długość, takie jak ciągi zakończone wartością null).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
