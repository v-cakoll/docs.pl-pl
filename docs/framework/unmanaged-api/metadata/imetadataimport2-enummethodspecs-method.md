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
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490723"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs — Metoda
Pobiera moduł wyliczający dla tablicy tokenów elementu MethodSpec skojarzonych z określonym tokenem MethodDef lub MemberRef.  
  
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
 [in. out] Wskaźnik do modułu wyliczającego dla elementu `rMethodSpecs` .  
  
 `tk`  
 podczas Token elementu MemberRef lub MethodDef reprezentujący metodę, której tokeny elementu MethodSpec mają zostać wyliczone. Jeśli wartość `tk` jest równa 0 (zero), wszystkie tokeny elementu MethodSpec w zakresie zostaną wyliczone.  
  
 `rMethodSpecs`  
 określoną Tablica tokenów elementu MethodSpec do wyliczenia.  
  
 `cMax`  
 podczas Żądana Maksymalna liczba tokenów do umieszczenia `rMethodSpecs` .  
  
 `pcMethodSpecs`  
 określoną Zwrócona liczba tokenów umieszczonych w `rMethodSpecs` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`pomyślnie zwrócono.|  
|`S_FALSE`|`phEnum`nie ma elementów członkowskich. W tym przypadku `pcMethodSpecs` jest ustawiona na 0 (zero).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
