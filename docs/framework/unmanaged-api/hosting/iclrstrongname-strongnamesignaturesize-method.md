---
title: ICLRStrongName::StrongNameSignatureSize — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c81b51deb6affb3dd39677184ea0a4b2e6ff61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219983"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>ICLRStrongName::StrongNameSignatureSize — Metoda
Zwraca rozmiar podpisu silnej nazwy. Ta metoda jest zwykle używana przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku, podczas tworzenia zestawu podpisanego z opóźnieniem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 [in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [in] Rozmiar w bajtach z `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [in] Liczba bajtów potrzebnych do przechowania podpisu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
