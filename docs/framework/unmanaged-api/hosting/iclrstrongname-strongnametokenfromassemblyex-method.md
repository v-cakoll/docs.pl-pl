---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: f08006c532d2778de67a4bab09623d248362535c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937426"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a>ICLRStrongName::StrongNameTokenFromAssemblyEx — Metoda
Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny, który reprezentuje token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.  
  
 `ppbStrongNameToken`  
 określoną Zwrócony token silnej nazwy.  
  
 `pcbStrongNameToken`  
 określoną Rozmiar (w bajtach) tokenu silnej nazwy.  
  
 `ppbPublicKeyBlob`  
 określoną Zwrócony klucz publiczny.  
  
 `pcbPublicKeyBlob`  
 określoną Rozmiar (w bajtach) klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona postać klucza publicznego. Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu. Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.  
  
 Po pobraniu klucza i utworzeniu tokenu należy wywołać metodę [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) , aby zwolnić przydzieloną pamięć.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromAssembly, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
