---
title: Funkcja CertTimestampAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="certtimestampauthenticodelicense-function"></a>Funkcja CertTimestampAuthenticodeLicense
Sygnatury czasowe jako Authenticode XrML licencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSignedLicenseBlob`  
 [in] Podpisem Authenticode XrML licencji za sygnaturami czasowymi. Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `pwszTimestampURI`  
 [in] Identyfikator URI serwera sygnatury czasowej.  
  
 `pTimestampSignatureBlob`  
 [out] Wskaźnik do CRYPT_DATA_BLOB do odbierania podpisu sygnatury czasowej algorytmem Base64. Wywołującego odpowiedzialność za wolny `pTimestampSignatureBlob` -> `pbData` z `HepFree()` po użyciu. Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
## <a name="remarks"></a>Uwagi  
 Podpis sygnatury czasowej jest rzeczywiście komunikat PKCS #7 SignedData, którego zawartość jest Forma binarna SignatureValue z nim licencja podpisu. Zasadniczo to dodatkowe zaradczych podpis licencji.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja zakończy się powodzeniem. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
