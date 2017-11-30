---
title: "IMetaDataImport::EnumMethodSemantics — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d5ec79701f73b8beb7759d72b972fc347a339c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics — Metoda
Wylicza właściwości i zdarzenia zmiany właściwości, których dotyczy określonej metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwsze wywołanie tej metody.  
  
 `mb`  
 [in] Token MethodDef, który ogranicza zakres wyliczenia.  
  
 `rEventProp`  
 [out] Tablica używany do przechowywania zdarzeń lub właściwości.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rEventProp` tablicy.  
  
 `pcEventProp`  
 [out] Liczba zdarzeń lub właściwości zwracane w `rEventProp`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych zdarzeń lub właściwości do wyliczenia. W takim przypadku `pcEventProp` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Zdefiniuj wiele typów środowiska uruchomieniowego języka wspólnego *właściwości* `Changed` zdarzeń i `On` *właściwości* `Changed` metody odnoszące się do ich właściwości. Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definiuje typ <xref:System.Windows.Forms.Control.Font%2A> właściwości, <xref:System.Windows.Forms.Control.FontChanged> zdarzenia i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody. Metoda dostępu set <xref:System.Windows.Forms.Control.Font%2A> wywołaniach właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę, która z kolei wywołuje <xref:System.Windows.Forms.Control.FontChanged> zdarzeń. Możesz wywołać `EnumMethodSemantics` przy użyciu elementu MethodDef dla <xref:System.Windows.Forms.Control.OnFontChanged%2A> można pobrać odwołań do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
