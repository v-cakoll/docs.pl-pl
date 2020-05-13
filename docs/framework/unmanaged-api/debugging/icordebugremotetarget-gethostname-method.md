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
ms.openlocfilehash: 020724c422af7cba0165e6f37d0eacb7742153ec
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379273"
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
 podczas Rozmiar (w znakach) `szHostName` buforu. Jeśli ten parametr ma wartość 0 (zero), `szHostName` musi mieć wartość null.  
  
 `pcchHostName`  
 określoną Liczba znaków, łącznie z terminatorem wartości null, w nazwie hosta lub adresie IP. Ten parametr może mieć wartość null.  
  
 `szHostName`  
 określoną Bufor, który zawiera nazwę hosta lub adres IP.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Nazwa hosta lub adres IP zostały pomyślnie zwrócone.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można zwrócić nazwy hosta lub adresu IP.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez składnik zapisywania debugera. Musi być zgodna z wieloma modelami wywołań: przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null do obu `cchHostName` i i `szHostName` `pcchHostName` zwraca rozmiar wymaganego buforu. W drugim wywołaniu zostanie przekazana poprzednio zwrócony rozmiar `cchHostName` , a bufor o odpowiednim rozmiarze jest przekazano `szHostName` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 3,5 SP1  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugRemoteTarget — Interfejs](icordebugremotetarget-interface.md)
- [ICorDebug — Interfejs](icordebug-interface.md)
