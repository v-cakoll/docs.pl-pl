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
ms.openlocfilehash: 13c1c505d939c1048eebef3d1d6b2abe493d319e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937421"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey — Metoda
Pobiera token reprezentujący klucz publiczny. Token silnej nazwy to skrócona postać klucza publicznego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 podczas Struktura typu [PublicKeyBlob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 podczas Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 określoną Token silnej nazwy odpowiadający kluczowi przesłanemu `pbPublicKeyBlob`. Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w której ma zostać zwrócony token. Obiekt wywołujący musi zwolnić tę pamięć przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbStrongNameToken`  
 określoną Rozmiar (w bajtach) zwracanego tokenu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy jest skróconą formą klucza publicznego, który służy do oszczędzania miejsca podczas zapisywania informacji o kluczu w metadanych. W odniesieniu do zestawu zależnego w odwołaniach do zestawów są używane tokeny silnej nazwy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob, struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
