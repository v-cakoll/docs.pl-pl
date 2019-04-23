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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196206"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes — Metoda
Wylicza tokeny niestandardowe definicja atrybutu skojarzone z określonego typu lub składowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [out w] Wskaźnik do zwróconego modułu wyliczającego.  
  
 `tk`  
 [in] Token do zakresu wyliczenia lub wartość zero dla wszystkich atrybutów niestandardowych.  
  
 `tkType`  
 [in] Token dla konstruktora typu atrybutów, które mają zostać wyliczone, lub `null` dla wszystkich typów.  
  
 `rCustomAttributes`  
 [out] Tablica atrybutów niestandardowych.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rCustomAttributes` tablicy.  
  
 `pcCustomAttributes`  
 [out, opcjonalny] Rzeczywista liczba tokenów wartości zwracanych w `rCustomAttributes`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` pomyślnie zwrócił.|  
|`S_FALSE`|Nie istnieją żadne atrybuty niestandardowe do wyliczenia. W takim przypadku `pcCustomAttributes` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
