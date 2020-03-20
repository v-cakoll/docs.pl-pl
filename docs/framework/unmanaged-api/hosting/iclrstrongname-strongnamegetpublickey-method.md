---
title: ICLRStrongName::StrongNameGetPublicKey — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181938"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey — Metoda
Pobiera klucz publiczny z pary klucza publicznego/prywatnego. Para kluczy może być podana jako nazwa kontenera klucza w dostawcy usług kryptograficznych (CSP) lub jako nieprzetworzona kolekcja bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szKeyContainer`  
 [w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych. Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach usługi CSP. W takim przypadku [metoda ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA). Żadne inne typy kluczy są obecnie obsługiwane.  
  
 `pbKeyBlob`  
 [w] Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32. Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.  
  
 `cbKeyBlob`  
 [w] Rozmiar w bajtach `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [na zewnątrz] Zwrócony obiekt BLOB klucza publicznego. Parametr `ppbPublicKeyBlob` jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego. Wywołujący musi zwolnić pamięć przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.  
  
 `pcbPublicKeyBlob`  
 [na zewnątrz] Rozmiar zwracanego obiektu BLOB klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameTokenFromPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob — Struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
