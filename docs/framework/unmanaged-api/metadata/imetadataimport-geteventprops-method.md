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
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437583"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps — Metoda
Pobiera informacje o metadanych dla zdarzenia reprezentowanego przez określony token zdarzenia, w tym typ deklarujący, metody dodawania i usuwania dla delegatów oraz wszelkie flagi i inne skojarzone dane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Token metadanych zdarzenia, który reprezentuje zdarzenie, dla którego mają zostać pobrane metadane.  
  
 `pClass`  
 określoną Wskaźnik do tokenu TypeDef reprezentujący klasę, która deklaruje zdarzenie.  
  
 `szEvent`  
 określoną Nazwa zdarzenia, do którego odwołuje się `ev`.  
  
 `pchEvent`  
 podczas Wymagana długość w szerokich znakach `szEvent`.  
  
 `pdwEventFlags`  
 określoną Długość zwrócona w postaci znaków dwubajtowych `szEvent`.  
  
 `ptkEventType`  
 określoną Wskaźnik do tokenu metadanych elementu TypeRef lub TypeDef reprezentujący typ <xref:System.Delegate> zdarzenia.  
  
 `pmdAddOn`  
 określoną Wskaźnik do tokenu metadanych reprezentującej metodę, która dodaje procedury obsługi dla zdarzenia.  
  
 `pmdRemoveOn`  
 określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która usuwa procedury obsługi dla zdarzenia.  
  
 `pmdFire`  
 określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która wywołuje zdarzenie.  
  
 `rmdOtherMethod`  
 określoną Tablica wskaźników tokenów z innymi metodami skojarzonymi ze zdarzeniem.  
  
 `cMax`  
 podczas Maksymalny rozmiar tablicy `rmdOtherMethod`.  
  
 `pcOtherMethod`  
 określoną Liczba tokenów zwróconych w `rmdOtherMethod`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
