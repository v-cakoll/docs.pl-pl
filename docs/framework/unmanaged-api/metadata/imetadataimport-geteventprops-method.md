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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491306"
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
 określoną Nazwa zdarzenia, do którego odwołuje się `ev` .  
  
 `pchEvent`  
 podczas Żądana długość w postaci znaków dwubajtowych `szEvent` .  
  
 `pdwEventFlags`  
 określoną Długość zwrócona w znaki dwubajtowe z `szEvent` .  
  
 `ptkEventType`  
 określoną Wskaźnik do tokenu metadanych elementu TypeRef lub TypeDef reprezentujący <xref:System.Delegate> Typ zdarzenia.  
  
 `pmdAddOn`  
 określoną Wskaźnik do tokenu metadanych reprezentującej metodę, która dodaje procedury obsługi dla zdarzenia.  
  
 `pmdRemoveOn`  
 określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która usuwa procedury obsługi dla zdarzenia.  
  
 `pmdFire`  
 określoną Wskaźnik do tokenu metadanych reprezentująca metodę, która wywołuje zdarzenie.  
  
 `rmdOtherMethod`  
 określoną Tablica wskaźników tokenów z innymi metodami skojarzonymi ze zdarzeniem.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rmdOtherMethod` tablicy.  
  
 `pcOtherMethod`  
 określoną Liczba tokenów zwróconych w `rmdOtherMethod` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
