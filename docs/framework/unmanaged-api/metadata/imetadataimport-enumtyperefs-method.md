---
title: "IMetaDataImport::EnumTypeRefs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 890f70900f2a1d4909d1511791d4d22bb81d3a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtyperefs-method"></a>IMetaDataImport::EnumTypeRefs — Metoda
Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwsze wywołanie tej metody.  
  
 `rTypeRefs`  
 [out] Tablica używany do przechowywania tokenów TypeRef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rTypeRefs` tablicy.  
  
 `pcTypeRefs`  
 [out] Wskaźnik do liczby tokenów TypeRef zwracane w `rTypeRefs`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim przypadku `pcTypeRefs` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 TypeRef token reprezentuje odwołanie do typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
