---
title: IMetaDataImport::EnumMethodSemantics — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175463"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics — Metoda
Wylicza właściwości i zdarzenia zmiany właściwości, z którymi jest powiązana określona metoda.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza. Musi to być null dla pierwszego wywołania tej metody.  
  
 `mb`  
 [w] Token MethodDef, który ogranicza zakres wyliczenia.  
  
 `rEventProp`  
 [na zewnątrz] Tablica używana do przechowywania zdarzeń lub właściwości.  
  
 `cMax`  
 [w] Maksymalny rozmiar `rEventProp` tablicy.  
  
 `pcEventProp`  
 [na zewnątrz] Liczba zdarzeń lub właściwości zwróconych w `rEventProp`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych zdarzeń lub właściwości do wyliczenia. W takim `pcEventProp` przypadku wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Wiele typowych typów środowiska uruchomieniowego języka *zdefiniować zdarzenia właściwości* `Changed` i `On`metody *właściwości* `Changed` związane z ich właściwości. Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definiuje <xref:System.Windows.Forms.Control.Font%2A> właściwość, <xref:System.Windows.Forms.Control.FontChanged> zdarzenie i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę. Set metody <xref:System.Windows.Forms.Control.Font%2A> akcesora <xref:System.Windows.Forms.Control.OnFontChanged%2A> właściwości wywołuje metodę, <xref:System.Windows.Forms.Control.FontChanged> która z kolei wywołuje zdarzenie. Wywołanie `EnumMethodSemantics` przy użyciu MethodDef, <xref:System.Windows.Forms.Control.OnFontChanged%2A> aby uzyskać <xref:System.Windows.Forms.Control.Font%2A> odwołania <xref:System.Windows.Forms.Control.FontChanged> do właściwości i zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
