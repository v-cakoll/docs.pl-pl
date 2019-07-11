---
title: Init — Metoda
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 606809533010f458272cd6fbbad6234217bddea2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741617"
---
# <a name="init-method"></a>Init — Metoda
Przygotowuje obiektów Implementowanie [ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) do użycia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pDispenser`  
 [Imetadatadispenserex — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) wskaźnik do rozdzielacz metadanych.  
  
 `pErrorHandler`  
 [Imetadataerror — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) wskaźnik do opcjonalne błąd obsługi interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
