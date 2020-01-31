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
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791944"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName — Metoda
Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 maszyny docelowej zdalnego debugowania. Protokół IPV6 nie jest w tej chwili obsługiwany.  
  
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
 podczas Rozmiar, w znakach, buforu `szHostName`. Jeśli ten parametr ma wartość 0 (zero), `szHostName` musi mieć wartość null.  
  
 `pcchHostName`  
 określoną Liczba znaków, łącznie z terminatorem wartości null, w nazwie hosta lub adresie IP. Ten parametr może mieć wartość null.  
  
 `szHostName`  
 określoną Bufor, który zawiera nazwę hosta lub adres IP.  
  
## <a name="return-value"></a>Wartość zwrócona  
 S_OK  
 Nazwa hosta lub adres IP zostały pomyślnie zwrócone.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można zwrócić nazwy hosta lub adresu IP.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez składnik zapisywania debugera. Musi być zgodna z wieloma modelami wywołań: przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null do obu `cchHostName` i `szHostName`, a `pcchHostName` zwraca rozmiar wymaganego buforu. W drugim wywołaniu rozmiar, który został wcześniej zwrócony, jest przesyłany w `cchHostName`, a bufor o odpowiednim rozmiarze jest przekazana w `szHostName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 3,5 SP1  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRemoteTarget, interfejs](icordebugremotetarget-interface.md)
- [ICorDebug, interfejs](icordebug-interface.md)
