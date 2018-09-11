---
title: ICLRStrongName::StrongNameTokenFromPublicKey — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98c0dbbbe65d8f8c0b0196c82db1a8fd2b0ee3dd
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273995"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey — Metoda
Pobiera token, który reprezentuje klucz publiczny. Token silna nazwa jest skrócona forma klucza publicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [in] Rozmiar w bajtach z `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Przekazany token silną nazwę odpowiadającą kluczowi `pbPublicKeyBlob`. Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w których ma zostać zwrócony token. Obiekt wywołujący musi zwolnić ta pamięć przy użyciu [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.  
  
 `pcbStrongNameToken`  
 [out] Rozmiar w bajtach, token zwrócony silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Token silna nazwa jest skrócona forma kluczem publicznym, używanego w taki sposób, aby zaoszczędzić miejsce, gdy kluczowe informacje są przechowywane w metadanych. W szczególności tokenów silnych nazw są używane w odwołania do zestawów do odwoływania się do zestawu zależnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** dołączony jako zasób w mscoree.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [PublicKeyBlob, struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
