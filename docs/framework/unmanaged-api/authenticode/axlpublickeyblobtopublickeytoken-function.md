---
title: Funkcja _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4d720480e4c8b21b3aa56ce81634a26ac9c75de
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776672"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken, funkcja
Oblicza token klucza publicznego o silnej nazwie w formacie PublicKeyBlob — dostawcy usług kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 podczas Obiekt BLOB klucza publicznego dostawcy usług kryptograficznych.  
  
 `ppwszPublicKeyHash`  
 określoną Wskaźnik do WCHAR *, aby otrzymać skrót klucza publicznego zakodowany szesnastkowo.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja się powiedzie; w `S_FALSE`przeciwnym razie.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
