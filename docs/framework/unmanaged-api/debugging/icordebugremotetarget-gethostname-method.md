---
title: ICorDebugRemoteTarget::GetHostName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43a502682e6ccfc36931970d0121f91529f51711
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744726"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName — Metoda
Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 zdalnego debugowania komputera docelowego. Protokół IPv6 nie jest obsługiwany w tej chwili.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Parametry  
 `cchHostName`  
 [in] Rozmiar, w postaci, z `szHostName` buforu. Jeśli ten parametr ma wartość 0 (zero), `szHostName` może mieć wartości null.  
  
 `pcchHostName`  
 [out] Liczba znaków, łącznie z terminatorem null, nazwa hosta lub adres IP. Ten parametr może mieć wartości null.  
  
 `szHostName`  
 [out] Bufor, który zawiera nazwę hosta lub adres IP.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Nazwa hosta lub adres IP została pomyślnie zwrócona.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można zwrócić nazwy hosta lub adres IP.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący debugera. Musi on być zgodny z paradygmatu wielokrotnego wywołania: Przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null na wartość oba `cchHostName` i `szHostName`, i `pcchHostName` zwraca rozmiar wymaganego buforu. Przy drugim wywołaniu, rozmiar, który został wcześniej zwrócony jest przekazywany w `cchHostName`, i właściwy rozmiar buforu jest przekazywany w `szHostName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRemoteTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
