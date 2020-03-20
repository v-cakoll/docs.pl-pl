---
title: IMetaDataImport::EnumCustomAttributes — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175528"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes — Metoda
Wylicza tokeny niestandardowej definicji atrybutów skojarzone z określonym typem lub elementem członkowskim.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do zwróconego wylicznika.  
  
 `tk`  
 [w] Token dla zakresu wyliczenia lub zero dla wszystkich atrybutów niestandardowych.  
  
 `tkType`  
 [w] Token dla konstruktora typu atrybutów, które mają być `null` wyliczone lub dla wszystkich typów.  
  
 `rCustomAttributes`  
 [na zewnątrz] Tablica niestandardowych tokenów atrybutów.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rCustomAttributes` tablicy.  
  
 `pcCustomAttributes`  
 [out, opcjonalnie] Rzeczywista liczba wartości tokenów zwrócona w `rCustomAttributes`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych atrybutów niestandardowych do wyliczenia. W takim `pcCustomAttributes` przypadku wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
