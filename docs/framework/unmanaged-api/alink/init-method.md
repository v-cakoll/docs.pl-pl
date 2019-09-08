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
ms.openlocfilehash: bf96770dd58c9b84596c082a615f626ec723cc6c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787246"
---
# <a name="init-method"></a>Init — Metoda
Przygotowuje obiekty implementujące [interfejs IALink —](ialink-interface.md) do użytku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pDispenser`  
 Wskaźnik [interfejsu IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) do rozdzielacza metadanych.  
  
 `pErrorHandler`  
 Wskaźnik [interfejsu IMetaDataError](../metadata/imetadataerror-interface.md) do opcjonalnego interfejsu obsługi błędów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
