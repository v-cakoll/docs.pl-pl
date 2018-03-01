---
title: "IMetaDataFilter — Interfejs"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0918802a146940fb7579279e56f752bd114c746c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter — Interfejs
Udostępnia metody dla oznaczenie i Filtrowanie tokenów metadanych, aby uniknąć powtarzania działania, które zostały już wykonane.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IsTokenMarked, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Pobiera wartość wskazującą, czy token określonych metadanych została przetworzona.|  
|[MarkToken, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Ustawia wartość wskazującą przetworzeniu token określonych metadanych.|  
|[UnmarkAll, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Usuwa znaczniki przetwarzania z wszystkich tokenów w bieżącym zakresie metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
