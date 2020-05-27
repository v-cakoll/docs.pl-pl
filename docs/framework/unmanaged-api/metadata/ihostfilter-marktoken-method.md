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
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008225"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken — Metoda
Wskazuje, że określony token metadanych zostanie przetworzony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 podczas Token metadanych do przetworzenia.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj token ma być przetwarzany, jeśli znajduje się w zakresie metadanych. `MarkToken`Metoda jest przenoszona do aparatu metadanych za pośrednictwem metody [IMetaDataEmit:: sethandlee](imetadataemit-sethandler-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy metadanych](metadata-interfaces.md)
- [IHostFilter — Interfejs](ihostfilter-interface.md)
