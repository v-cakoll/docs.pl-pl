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
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099904"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_funkcja AxlPublicKeyBlobToPublicKeyToken
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
 `S_OK`, jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
