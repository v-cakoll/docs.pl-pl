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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177269"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps — Metoda
Pobiera informacje o metadanych dla zdarzenia reprezentowane przez token określonego zdarzenia, w tym typ deklarowania, dodawanie i usuwanie metod delegatów i wszelkie flagi i inne skojarzone dane.  
  
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
 [w] Token metadanych zdarzenia reprezentujący zdarzenie, dla które można uzyskać metadane.  
  
 `pClass`  
 [na zewnątrz] Wskaźnik do TypeDef token reprezentujący klasę, która deklaruje zdarzenie.  
  
 `szEvent`  
 [na zewnątrz] Nazwa zdarzenia, do którego `ev`odwołuje się .  
  
 `pchEvent`  
 [w] Żądana długość w szerokich znakach `szEvent`.  
  
 `pdwEventFlags`  
 [na zewnątrz] Zwrócona długość w `szEvent`szerokich znakach .  
  
 `ptkEventType`  
 [na zewnątrz] Wskaźnik do typeref lub TypeDef token metadanych reprezentujących <xref:System.Delegate> typ zdarzenia.  
  
 `pmdAddOn`  
 [na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która dodaje programy obsługi dla zdarzenia.  
  
 `pmdRemoveOn`  
 [na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która usuwa programy obsługi dla zdarzenia.  
  
 `pmdFire`  
 [na zewnątrz] Wskaźnik do tokenu metadanych reprezentujący metodę, która wywołuje zdarzenie.  
  
 `rmdOtherMethod`  
 [na zewnątrz] Tablica wskaźników tokenu do innych metod skojarzonych ze zdarzeniem.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rmdOtherMethod` tablicy.  
  
 `pcOtherMethod`  
 [na zewnątrz] Liczba tokenów zwróconych `rmdOtherMethod`w .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
