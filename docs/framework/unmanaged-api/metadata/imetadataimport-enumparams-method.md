---
title: IMetaDataImport::EnumParams — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: f9a58a70b5264d7f1eb33fb0e09c702c94a13e85
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491770"
---
# <a name="imetadataimportenumparams-method"></a>IMetaDataImport::EnumParams — Metoda
Wylicza tokeny ParamDef reprezentujące parametry metody przywoływanej przez określony token MethodDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego. Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.  
  
 `mb`  
 podczas Token MethodDef reprezentujący metodę z parametrami do wyliczenia.  
  
 `rParams`  
 określoną Tablica służąca do przechowywania tokenów ParamDef.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rParams` tablicy.  
  
 `pcTokens`  
 określoną Liczba tokenów ParamDef zwróconych w `rParams` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumParams`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów do wyliczenia. W takim przypadku `pcTokens` jest równa zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
