---
title: ICLRValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178061"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate — Metoda
Sprawdza poprawność przenośnego pliku wykonywalnego (PE) lub języka pośredniego firmy Microsoft (MSIL) w określonym pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a>Parametry  
 `veh`  
 [w] Wskaźnik do `IVEHandler` wystąpienia, który obsługuje błędy sprawdzania poprawności.  
  
 `ulAppDomainId`  
 [w] Identyfikator bieżącego <xref:System.AppDomain>.  
  
 `ulFlags`  
 [w] Kombinacja [Wartości ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wskazując rodzaj sprawdzania poprawności, które należy wykonać.  
  
 `ulMaxError`  
 [w] Maksymalna liczba błędów, które należy zezwolić przed zamknięciem sprawdzania poprawności.  
  
 `token`  
 [w] Nieużywane.  
  
 `fileName`  
 [w] Nazwa pliku, który ma zostać zweryfikowany.  
  
 `pe`  
 [w] Wskaźnik do buforu plików.  
  
 `ulSize`  
 [w] Rozmiar w bajtach pliku, który ma zostać zweryfikowany.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Validate`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRValidator, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
