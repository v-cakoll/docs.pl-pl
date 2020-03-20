---
title: IMetaDataImport::EnumTypeRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175437"
---
# <a name="imetadataimportenumtyperefs-method"></a>IMetaDataImport::EnumTypeRefs — Metoda
Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza. Musi to być null dla pierwszego wywołania tej metody.  
  
 `rTypeRefs`  
 [na zewnątrz] Tablica używana do przechowywania tokenów TypeRef.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rTypeRefs` tablicy.  
  
 `pcTypeRefs`  
 [na zewnątrz] Wskaźnik do liczby tokenów TypeRef `rTypeRefs`zwróconych w .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim `pcTypeRefs` przypadku wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Token TypeRef reprezentuje odwołanie do typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
