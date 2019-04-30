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
ms.openlocfilehash: 4749bfee22e58ad7c3ca29ec992da88493ca2c5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763844"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual — Metoda
Pobiera blok pamięci ciągłej uruchamianie pod podanym adresem i zwraca go w dostarczony bufor.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] Początkowy adres żądanej pamięci.  
  
 `pbuffer`  
 [out] Bufor, w którym będzie przechowywana pamięć.  
  
 `bytesRequested`  
 [in] Liczba bajtów, które można pobrać z adresu docelowego.  
  
 `pBytesRead`  
 [out] Liczba bajtów odczytanych w rzeczywistości z adres docelowy. Może to być krótsza niż `bytesRequested`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli pierwszy bajt (pod adresem początkową) może zostać odczytany, wywołanie powinno zwrócić Powodzenie (umożliwiających wydajne odczytywania struktury danych z własnym opisem długości, takich jak ciągi zakończone wartością null).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
