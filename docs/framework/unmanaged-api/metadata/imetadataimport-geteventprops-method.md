---
title: "IMetaDataImport::GetEventProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps — Metoda
Pobiera metadane dla zdarzenia reprezentowany przez token określonego zdarzenia, w tym typ deklarujący, Dodaj i Usuń metody delegatów i flagi oraz inne powiązane dane.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `ev`  
 [in] Token metadanych zdarzeń reprezentujący zdarzeń można pobrać metadanych.  
  
 `pClass`  
 [out] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenia.  
  
 `szEvent`  
 [out] Nazwa zdarzenia odwołuje się `ev`.  
  
 `pchEvent`  
 [in] Żądana długość w znakach szerokości `szEvent`.  
  
 `pdwEventFlags`  
 [out] Długość zwróconych w znaki dwubajtowe `szEvent`.  
  
 `ptkEventType`  
 [out] Wskaźnik do elementu TypeRef lub TypeDef metadanych token reprezentujący <xref:System.Delegate> typ zdarzenia.  
  
 `pmdAddOn`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje obsługę zdarzenia.  
  
 `pmdRemoveOn`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.  
  
 `pmdFire`  
 [out] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenie.  
  
 `rmdOtherMethod`  
 [out] Tablica tokenu wskaźników do innych metod, skojarzone ze zdarzeniem.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rmdOtherMethod` tablicy.  
  
 `pcOtherMethod`  
 [out] Liczba tokenów zwracanych w `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
