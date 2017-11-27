---
title: "ICLRStrongName::StrongNameGetPublicKey — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b7ace87a5eff5235d85507bda649e55ea18fd93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey — Metoda
Pobiera klucz publiczny z pary kluczy publiczny/prywatny. Pary kluczy można podać jako nazwa kontenera klucza dostawcy usług kryptograficznych (CSP) lub jako kolekcję pierwotnych bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szKeyContainer`  
 [in] Nazwa kontenera klucza, który zawiera pary kluczy publiczny/prywatny. Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług Kryptograficznych. W takim przypadku [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) metody wyodrębnia klucza publicznego z pary kluczy przechowywanych w kontenerze.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w klucza dużego obiektu binarnego (BLOB).  
  
 Klucze muszą być Rivest-Shamir-Adleman (RSA 1024-bitowe) kluczy podpisywania. Żadne inne typy klucze są obsługiwane w tej chwili.  
  
 `pbKeyBlob`  
 [in] Wskaźnik do pary kluczy publiczny/prywatny. Tej pary jest w formacie utworzone przez Win32 `CryptExportKey` funkcji. Jeśli `pbKeyBlob` jest null, określony przez kontener klucza `szKeyContainer` założono, że zawiera pary kluczy.  
  
 `cbKeyBlob`  
 [in] Rozmiar w bajtach z `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] Zwrócony klucza publicznego obiektu BLOB. `ppbPublicKeyBlob` Parametr jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego. Obiekt wywołujący musi zwolnić pamięć przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.  
  
 `pcbPublicKeyBlob`  
 [out] Rozmiar zwróconego obiektu BLOB klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).  
  
## <a name="remarks"></a>Uwagi  
 Klucz publiczny jest zawarta w [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameTokenFromPublicKey — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [Publickeyblob — struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
