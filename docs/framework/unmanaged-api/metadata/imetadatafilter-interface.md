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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4196ff2cb2d4ebc401076f603a8a7fdc9b9c76ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049963"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter — Interfejs
Zawiera metody służące do oznaczenia i filtrowanie tokeny metadanych, aby uniknąć powtarzania czynności, które już zostały podjęte.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IsTokenMarked, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Pobiera wartość wskazującą, czy token określonych metadanych została przetworzona.|  
|[MarkToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Ustawia wartość wskazującą, przetworzeniu token określonych metadanych.|  
|[UnmarkAll, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Usuwa znaki przetwarzania z wszystkich tokenów w bieżącym zakresie metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
