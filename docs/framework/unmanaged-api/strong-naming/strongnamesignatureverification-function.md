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
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129230"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification — Funkcja
Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera sygnaturę silnej nazwy, która jest sprawdzana według określonych flag.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureVerification —](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .  
  
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
 podczas Ścieżka do przenośnego pliku wykonywalnego (. dll lub. exe) dla zestawu do zweryfikowania.  
  
 `dwInFlags`  
 podczas Flagi modyfikujące zachowanie weryfikacji. Obsługiwane są następujące wartości:  
  
- `SN_INFLAG_FORCE_VER` (0x00000001) — wymusza weryfikację, nawet jeśli jest konieczna przesłonięcie ustawień rejestru.  
  
- `SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to pierwsze sprawdzenie manifestu.  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna będzie zezwalać na dostęp tylko użytkownikom z uprawnieniami administracyjnymi.  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna nie będzie zapewniać żadnych gwarancji ograniczenia dostępu.  
  
- `SN_INFLAG_RUNTIME` (0x80000000) — zarezerwowane na potrzeby debugowania wewnętrznego.  
  
 `pdwOutFlags`  
 określoną Flagi wskazujące, czy podpis silnej nazwy został zweryfikowany. Obsługiwana jest następująca wartość:  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest ustawiona na `false`, aby określić, że weryfikacja powiodła się z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureVerification, metoda](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx, metoda](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
