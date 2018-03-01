---
title: "ImportTypes2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a>ImportTypes2 — Metoda
Inicjuje importowanie typów. Wywołanie tej metody ma się zacząć importowanie typów z każdym zakresem importować za pomocą [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu, do których ma zostać zaimportowany.  
  
 `FileToken`  
 Identyfikator pliku, z którego będą importowane.  
  
 `dwScope`  
 Liczony od zera zakres, z którego będą importowane.  
  
 `phEnum`  
 Odbiera uchwytu modułu wyliczającego dla typów w danym zakresie.  
  
 `ppImportScope`  
 Opcjonalnie odbiera [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu.  
  
 `pdwCountOfTypes`  
 Opcjonalnie odbiera liczba typy w podanym zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
