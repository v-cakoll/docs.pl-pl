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
ms.openlocfilehash: 0e1975a5063217299ddbcdce6f625d5a1285d5b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642558"
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
