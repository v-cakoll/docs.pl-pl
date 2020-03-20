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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176958"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob — Struktura
Reprezentuje w formacie binarnym klucz publiczny pary klucza publicznego/prywatnego.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`SigAlgId`|Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w wincrypt.h) klucza publicznego.|  
|`HashAlgId`|Identyfikator algorytmu mieszania (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.|  
|`cbPublicKey`|Długość klucza w bajtach.|  
|`PublicKey`|Tablica bajtów o zmiennej długości, która zawiera wartość klucza w formacie zwracanym przez CryptoAPI.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura `PublicKeyBlob` jest używana przez [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)i inne silne funkcje nazwy do reprezentowania klucza publicznego pary klucza publicznego/prywatnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameGetPublicKey, funkcja](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration, funkcja](strongnamesignaturegeneration-function.md)
