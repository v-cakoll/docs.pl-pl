---
title: GetPublicKeyToken — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 851ff82a539ce354d5507e829d8c461a0f2494ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729476"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken — Metoda
Pobiera token klucza publicznego do pliku danego klucza lub kontenera kluczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszKeyFile`  
 Nazwa pliku klucza.  
  
 `pszKeyContainer`  
 Nazwa kontenera kluczy.  
  
 `pvPublicKeyToken`  
 Adres, gdzie token klucza ma być przechowywany.  
  
 `pcbPublicKeyToken`  
 Określa rozmiar w bajtach, bufor wskazywany przez `pvPublicKeyToken`. Po powrocie zawiera rzeczywista liczba bajtów używanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz także
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
