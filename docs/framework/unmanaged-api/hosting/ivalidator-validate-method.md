---
title: "IValidator::Validate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 722c6acc7e152a78ba28bc2730b2fdc7e0c45eb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate — Metoda
Weryfikuje określony przenośny plik wykonywalny (PE) lub plik języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `veh`  
 [in] Wskaźnik do `IVEHandler` wystąpienie, które obsługuje błędy sprawdzania poprawności.  
  
 `pAppDomain`  
 [in] Wskaźnik do ładowania pliku domeny aplikacji.  
  
 `ulFlags`  
 [in] Bitowe połączenie [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) wartości i wskazujący operacji sprawdzania poprawności, które powinny zostać wykonane.  
  
 `ulMaxError`  
 [in] Maksymalna liczba błędów umożliwia przed zakończeniem sprawdzania poprawności.  
  
 `token`  
 [in] Nie jest używany.  
  
 `fileName`  
 [in] Ciąg określający nazwę pliku, który ma zostać zweryfikowana.  
  
 `pe`  
 [in] Wskaźnik do bufora pamięci, w którym przechowywany jest plik.  
  
 `ulSize`  
 [in] Rozmiar w bajtach, pliku, który ma zostać zweryfikowana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator.idl, IValidator.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
