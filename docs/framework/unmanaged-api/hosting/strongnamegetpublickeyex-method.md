---
title: StrongNameGetPublicKeyEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176230"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx — Metoda
Pobiera klucz publiczny z pary klucza publicznego/prywatnego i określa algorytm mieszania i algorytm podpisu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzKeyContainer`  
 [w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych. Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP). W takim przypadku `StrongNameGetPublicKeyEx` metoda wyodrębnia klucz publiczny z pary kluczy przechowywanych w kontenerze.  
  
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
  
 `uHashAlgId`  
 [w] Algorytm mieszania zestawu. Zobacz uwagi sekcji listy zaakceptowanych wartości.  
  
 `uReserved`  
 [w] Zarezerwowane do wykorzystania w przyszłości; wartości null.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono zestaw `uHashAlgId` zaakceptowanych wartości dla parametru.  
  
|Nazwa|Wartość|  
|----------|-----------|  
|Brak|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameTokenFromPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob — Struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
