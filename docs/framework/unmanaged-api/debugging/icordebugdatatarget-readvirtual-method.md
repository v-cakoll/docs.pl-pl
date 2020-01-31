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
ms.openlocfilehash: 20cea94961a250c3981d892910da1dcee20a060b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783736"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual — Metoda
Pobiera blok ciągłej pamięci zaczynający się od określonego adresu i zwraca go w dostarczonym buforze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres początkowy żądanej pamięci.  
  
 `pbuffer`  
 określoną Bufor, w którym będzie przechowywana pamięć.  
  
 `bytesRequested`  
 podczas Liczba bajtów pobieranych z adresu docelowego.  
  
 `pBytesRead`  
 określoną Liczba bajtów faktycznie odczytywanych z adresu docelowego. Może to być mniejsze niż `bytesRequested`.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku odczytywania pierwszego bajtu (na określonym adresie początkowym) wywołanie powinno zwrócić sukces (w celu zapewnienia obsługi wydajnego odczytu struktur danych z unikatową długością, na przykład w przypadku ciągów zakończonych znakiem null).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget, interfejs](icordebugdatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
