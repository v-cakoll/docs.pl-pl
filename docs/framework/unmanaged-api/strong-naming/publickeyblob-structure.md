---
title: "PublicKeyBlob — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PublicKeyBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: PublicKeyBlob
helpviewer_keywords: PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b70ab9ee04ff2a060f3c66173a3628032afc0b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob — Struktura
Reprezentuje w formacie binarnym, klucz publiczny pary kluczy publiczny/prywatny.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`SigAlgId`|Identyfikator algorytmu podpisu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.|  
|`HashAlgId`|Identyfikator algorytmu wyznaczania wartości skrótu (typu `ALG_ID`, zgodnie z definicją w WinCrypt.h) klucza publicznego.|  
|`cbPublicKey`|Długość klucza w bajtach.|  
|`PublicKey`|Tablica bajtów o zmiennej długości, która zawiera wartości klucza w formacie zwracane przez interfejs CryptoAPI.|  
  
## <a name="remarks"></a>Uwagi  
 `PublicKeyBlob` Struktura jest używana przez [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)i inne funkcje silnej nazwy do reprezentowania klucz publiczny pary kluczy publiczny/prywatny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameGetPublicKey, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [StrongNameSignatureGeneration, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [Silne nazewnictwo struktury](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
