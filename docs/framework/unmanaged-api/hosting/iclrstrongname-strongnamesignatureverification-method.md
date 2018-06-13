---
title: ICLRStrongName::StrongNameSignatureVerification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e43f42d01bf61e8ab15fd45fa43329d71ba3b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435328"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>ICLRStrongName::StrongNameSignatureVerification — Metoda
Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy, która zostanie poddana weryfikacji zgodnie z określonym flagi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu można zweryfikować.  
  
 `dwInFlags`  
 [in] Flagi, aby zmodyfikować zachowanie weryfikacji. Obsługiwane są następujące wartości:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to plik manifestu jest weryfikowany po raz pierwszy.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna będzie zezwalał na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) — określa, czy zestaw będzie dostępny tylko dla bieżącego użytkownika.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, czy pamięć podręczna zapewni żadnych gwarancji ograniczeń dostępu.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.  
  
 `pdwOutFlags`  
 [out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy. Obsługiwane jest następującą wartość:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
