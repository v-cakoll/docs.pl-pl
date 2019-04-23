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
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147436"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>Funkcja _AxlPublicKeyBlobToPublicKeyToken
Oblicza silnej nazwy token klucza publicznego z formatu publickeyblob — dostawcy usług Kryptograficznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 [in] Dostawcy usług Kryptograficznych blob klucza publicznego.  
  
 `ppwszPublicKeyHash`  
 [out] Wskaźnik do WCHAR * do odbierania zakodowanego szesnastkowo skrótu klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
