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
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176321"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey — Metoda
Pobiera token, który reprezentuje klucz publiczny. Token silnej nazwy jest skróconą formą klucza publicznego.  
  
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
 [w] Struktura typu [PublicKeyBlob,](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [w] Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [na zewnątrz] Token silnej nazwy odpowiadający `pbPublicKeyBlob`kluczowi przekazanym w . Środowisko wykonawcze języka wspólnego przydziela pamięć, w której do zwrócenia tokenu. Wywołujący należy zwolnić tę pamięć przy użyciu [metody ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbStrongNameToken`  
 [na zewnątrz] Rozmiar w bajtach zwróconego tokenu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona forma klucza publicznego, który jest używany do zapisywania miejsca podczas przechowywania kluczowych informacji w metadanych. W szczególności tokeny silnej nazwy są używane w odwołaniach do zestawu w celu odwoływania się do zestawu zależnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob — Struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
