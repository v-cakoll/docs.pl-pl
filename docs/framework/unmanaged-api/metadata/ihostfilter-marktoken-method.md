---
title: IHostFilter::MarkToken — Metoda
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4a1761f088732cf19d55f42d66288bb281885f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589454"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken — Metoda
Wskazuje token określonych metadanych zostaną przetworzone.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token metadanych, które mają być przetwarzane.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj chcesz tokenu służącego do ich przetworzyć, jeśli znajduje się w zakresie metadanych. `MarkToken` Metody jest przekazywany do aparatu metadanych za pośrednictwem [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IHostFilter, interfejs](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
