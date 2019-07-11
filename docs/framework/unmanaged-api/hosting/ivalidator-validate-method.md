---
title: IValidator::Validate — Metoda
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 840a3779ca5692787c2c352db60a29d6a4d4ba4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768591"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate — Metoda
Sprawdza poprawność określonego pliku wykonalnego (PE) lub pliku języka intermediate language (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `veh`  
 [in] Wskaźnik do `IVEHandler` wystąpienia, która obsługuje błędy sprawdzania poprawności.  
  
 `pAppDomain`  
 [in] Wskaźnik do domeny aplikacji, w którym jest on ładowany.  
  
 `ulFlags`  
 [in] Bitowa kombinacja [validatorflags —](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości, wskazujący operacji sprawdzania poprawności, które powinny być wykonywane.  
  
 `ulMaxError`  
 [in] Maksymalna liczba błędów, aby umożliwić przed zakończeniem weryfikacji.  
  
 `token`  
 [in] Nie jest używany.  
  
 `fileName`  
 [in] Ciąg, który określa nazwę pliku, który ma zostać zweryfikowana.  
  
 `pe`  
 [in] Wskaźnik do bufora pamięci, w którym jest przechowywany plik.  
  
 `ulSize`  
 [in] Rozmiar w bajtach, plików, który ma zostać zweryfikowana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
