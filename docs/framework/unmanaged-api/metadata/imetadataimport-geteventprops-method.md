---
title: IMetaDataImport::GetEventProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 138be940c6a03fc58e488e344455946bdb832bab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214523"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps — Metoda
Pobiera informacje o metadanych dla zdarzenia, reprezentowane przez token określonego zdarzenia, w tym typ deklarujący, Dodaj i Usuń metody obiektów delegowanych, flag i inne powiązane dane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ev`  
 [in] Token metadanych zdarzenia reprezentujący zdarzeń, które można pobrać metadanych.  
  
 `pClass`  
 [out] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenie.  
  
 `szEvent`  
 [out] Nazwa zdarzenia odwołuje się `ev`.  
  
 `pchEvent`  
 [in] Żądana długość w znaków `szEvent`.  
  
 `pdwEventFlags`  
 [out] Zwrócona długość w znakach szerokiego `szEvent`.  
  
 `ptkEventType`  
 [out] Wskaźnik do TypeRef lub TypeDef metadanych token reprezentujący <xref:System.Delegate> typ zdarzenia.  
  
 `pmdAddOn`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje programy obsługi dla zdarzenia.  
  
 `pmdRemoveOn`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.  
  
 `pmdFire`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenia.  
  
 `rmdOtherMethod`  
 [out] Tablica wskaźników tokenu do innych metod, skojarzone ze zdarzeniem.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rmdOtherMethod` tablicy.  
  
 `pcOtherMethod`  
 [out] Liczba zwracane w tokenach `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
