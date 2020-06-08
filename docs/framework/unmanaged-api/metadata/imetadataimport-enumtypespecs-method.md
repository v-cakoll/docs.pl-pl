---
title: IMetaDataImport::EnumTypeSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503721"
---
# <a name="imetadataimportenumtypespecs-method"></a>IMetaDataImport::EnumTypeSpecs — Metoda
Wylicza tokeny elementu TypeSpec zdefiniowane w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego. Ta wartość musi być RÓWNa NULL dla pierwszego wywołania tej metody.  
  
 `rTypeSpecs`  
 określoną Tablica służąca do przechowywania tokenów elementu TypeSpec.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rTypeSpecs` tablicy.  
  
 `pcTypeSpecs`  
 określoną Liczba zwróconych tokenów elementu TypeSpec w `rTypeSpecs` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów do wyliczenia. W takim przypadku `pcTypeSpecs` jest równa zero.|  
  
## <a name="remarks"></a>Uwagi  
 Tokeny elementu TypeSpec są tworzone przez metodę [IMetaDataEmit:: GetTokenFromTypeSpec —](imetadataemit-gettokenfromtypespec-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
