---
title: IMetaDataFilter — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503799"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter — Interfejs
Zapewnia metody oznaczania i filtrowania tokenów metadanych, aby uniknąć powtarzających się akcji, które zostały już wykonane.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IsTokenMarked — Metoda](imetadatafilter-istokenmarked-method.md)|Pobiera wartość wskazującą, czy określony token metadanych został przetworzony.|  
|[MarkToken — Metoda](imetadatafilter-marktoken-method.md)|Ustawia wartość wskazującą, że określony token metadanych został przetworzony.|  
|[UnmarkAll — Metoda](imetadatafilter-unmarkall-method.md)|Usuwa znaczniki przetwarzania ze wszystkich tokenów w bieżącym zakresie metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](metadata-interfaces.md)
