---
title: StrongNameSignatureVerification — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3cd2a123e495b4bf19168e86932c866c91e980f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751632"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification — Funkcja
Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy, który jest weryfikowany zgodnie z określone flagi.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamesignatureverification —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu sprawdzić.  
  
 `dwInFlags`  
 [in] Flagi, aby zmodyfikować zachowanie weryfikacji. Obsługiwane są następujące wartości:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to manifest jest weryfikowany po raz pierwszy.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.  
  
 `pdwOutFlags`  
 [out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy. Obsługiwane jest następującą wartość:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli weryfikacja się powiodła. w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureVerification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
