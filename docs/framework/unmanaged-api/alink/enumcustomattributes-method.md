---
title: EnumCustomAttributes — Metoda
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b419962982fc80591ed565cceb28afb88a39495e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789977"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes — Metoda
Pobiera atrybuty niestandardowe na poziomie zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `hEnum`  
 Uchwyt modułu wyliczającego.  
  
 `tkType`  
 Typ atrybutów, które mają zostać wyliczone. Użyj `mdTokenNill` dla wszystkich atrybutów.  
  
 `rCustomValues`  
 Odbiera tokenów atrybutów niestandardowych.  
  
 `cMax`  
 Określa rozmiar `rCustomValues` tablicy.  
  
 `pcCustomValues`  
 Opcjonalnie odbiera token wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
