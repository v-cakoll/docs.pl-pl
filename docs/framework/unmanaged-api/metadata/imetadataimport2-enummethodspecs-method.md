---
title: IMetaDataImport2::EnumMethodSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177171"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs — Metoda
Pobiera wyliczenia dla tablicy Tokeny MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza `rMethodSpecs`dla .  
  
 `tk`  
 [w] The MemberRef lub MethodDef token, który reprezentuje metodę, której tokeny MethodSpec mają być wyliczone. Jeśli wartość `tk` wynosi 0 (zero), wszystkie tokeny MethodSpec w zakresie zostaną wyliczone.  
  
 `rMethodSpecs`  
 [na zewnątrz] Tablica tokenów MethodSpec do wyliczenia.  
  
 `cMax`  
 [w] Żądana maksymalna liczba tokenów `rMethodSpecs`do umieszczenia w .  
  
 `pcMethodSpecs`  
 [na zewnątrz] Zwrócona liczba tokenów `rMethodSpecs`umieszczonych w .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`zwrócono pomyślnie.|  
|`S_FALSE`|`phEnum`nie ma elementów członkowskich. W takim `pcMethodSpecs` przypadku jest ustawiona na 0 (zero).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
