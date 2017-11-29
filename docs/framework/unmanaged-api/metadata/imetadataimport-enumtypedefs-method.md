---
title: "IMetaDataImport::EnumTypeDefs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs — Metoda
Wylicza tokeny TypeDef reprezentujący wszystkie typy w bieżącym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [out] Wskaźnik do nowego modułu wyliczającego. Musi to być wartość NULL dla pierwsze wywołanie tej metody.  
  
 `rTypeDefs`  
 [in] Tablica używany do przechowywania tokenów TypeDef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rTypeDefs` tablicy.  
  
 `pcTypeDefs`  
 [out] Liczba tokenów TypeDef zwracane w `rTypeDefs`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim przypadku `pcTypeDefs` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 TypeDef token reprezentuje typ, takich jak klasy lub interfejsu, jak również żadnego typu dodane za pośrednictwem mechanizm rozszerzalności.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
