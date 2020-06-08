---
title: IMetaDataImport::EnumFields — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492281"
---
# <a name="imetadataimportenumfields-method"></a>IMetaDataImport::EnumFields — Metoda
Wylicza tokeny FieldDef dla typu, do którego odwołuje się określony token TypeDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego.  
  
 `cl`  
 podczas Token TypeDef klasy, której pola mają zostać wyliczone.  
  
 `rFields`  
 określoną Lista tokenów FieldDef.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rFields` tablicy.  
  
 `pcTokens`  
 określoną Rzeczywista liczba tokenów FieldDef zwrócona w `rFields` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumFields`pomyślnie zwrócono.|  
|`S_FALSE`|Brak pól do wyliczenia. W takim przypadku `pcTokens` jest równa zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
