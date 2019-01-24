---
title: ImportTypes2 — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60f2057330f1a06cdd3e6ff5560f8ca7aeefe857
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725730"
---
# <a name="importtypes2-method"></a>ImportTypes2 — Metoda
Inicjuje importowania typów. Wywołaj tę metodę ma się zacząć importowanie typów z każdym zakresem importowane za pośrednictwem [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
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
 Identyfikator zestawu, do którego chcesz zaimportować.  
  
 `FileToken`  
 Identyfikator pliku do, z którego chcesz zaimportować.  
  
 `dwScope`  
 Liczony od zera zakres, z którego chcesz zaimportować.  
  
 `phEnum`  
 Odbiera uchwytu modułu wyliczającego dla typów w danym zakresie.  
  
 `ppImportScope`  
 Opcjonalnie odbiera [imetadataimport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interfejsu.  
  
 `pdwCountOfTypes`  
 Opcjonalnie odbiera liczba typów w określonym zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
