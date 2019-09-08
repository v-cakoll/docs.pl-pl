---
title: PublicKeyBlob — Struktura
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799163"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob — Struktura
Reprezentuje w formacie binarnym klucz publiczny pary kluczy publiczny/prywatny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`SigAlgId`|Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt. h) klucza publicznego.|  
|`HashAlgId`|Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt. h) klucza publicznego.|  
|`cbPublicKey`|Długość klucza w bajtach.|  
|`PublicKey`|Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracanym przez interfejs CryptoAPI.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura jest używana przez [StrongNameGetPublicKey —](strongnamegetpublickey-function.md), StrongNameSignatureGeneration — i inne funkcje silnej nazwy do reprezentowania klucza publicznego pary kluczy publicznych/prywatnych. [](strongnamesignaturegeneration-function.md) `PublicKeyBlob`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameGetPublicKey, funkcja](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration, funkcja](strongnamesignaturegeneration-function.md)
