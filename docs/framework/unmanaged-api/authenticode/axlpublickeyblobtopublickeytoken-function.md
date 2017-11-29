---
title: Funkcja _AxlPublicKeyBlobToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlPublicKeyBlobToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a6a78fad95b894e82a75159458f25264f0ee0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>Funkcja _AxlPublicKeyBlobToPublicKeyToken
Oblicza silnej nazwy token klucza publicznego z formatu PUBLICKEYBLOB dostawcy usług Kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 [in] Publiczny blob klucza dostawcy usług Kryptograficznych.  
  
 `ppwszPublicKeyHash`  
 [out] Wskaźnik do WCHAR * do odbierania zakodowane w systemie szesnastkowym wartość skrótu klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja zakończy się pomyślnie; w przeciwnym razie `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
