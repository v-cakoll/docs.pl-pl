---
title: IMetaDataImport::EnumProperties — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b42c558009c25adfd7d282da905e7182dfd3342
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467027"
---
# <a name="imetadataimportenumproperties-method"></a>IMetaDataImport::EnumProperties — Metoda
Wylicza tokenów właściwości reprezentujących właściwości typu odwołuje się określony token TypeDef.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out w] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwszego wywołania tej metody.  
  
 `td`  
 [in] TypeDef token reprezentujący typ z właściwościami do wyliczenia.  
  
 `rProperties`  
 [out] Tablica do przechowywania tokenów właściwości.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rProperties` tablicy.  
  
 `pcProperties`  
 [out] Liczba tokenów właściwości zwracane w `rProperties`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych tokeny do wyliczenia. W takim przypadku `pcProperties` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
