---
title: IMetaDataImport::EnumFieldsWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177343"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName — Metoda
Wylicza tokeny FieldDef określonego typu o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza.  
  
 `cl`  
 [w] Token typu, którego pola mają być wyliczone.  
  
 `szName`  
 [w] Nazwa pola, która ogranicza zakres wyliczenia.  
  
 `rFields`  
 [na zewnątrz] Tablica używana do przechowywania tokenów FieldDef.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rFields` tablicy.  
  
 `pcTokens`  
 [na zewnątrz] Rzeczywista liczba tokenów FieldDef `rFields`zwrócona w .  
  
## <a name="remarks"></a>Uwagi  
 W przeciwieństwie do [IMetaDataImport::EnumFields,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md) `EnumFieldsWithName` odrzuca wszystkie tokeny pól, które nie mają określonej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych pól do wyliczenia. W takim `pcTokens` przypadku wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
