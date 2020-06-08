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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491930"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics — Metoda
Wylicza właściwości i zdarzenia zmiany właściwości, z którymi powiązana jest określona metoda.  
  
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
 [in. out] Wskaźnik do modułu wyliczającego. Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.  
  
 `mb`  
 podczas Token MethodDef, który ogranicza zakres wyliczania.  
  
 `rEventProp`  
 określoną Tablica służąca do przechowywania zdarzeń lub właściwości.  
  
 `cMax`  
 podczas Maksymalny rozmiar `rEventProp` tablicy.  
  
 `pcEventProp`  
 określoną Liczba zwróconych zdarzeń lub właściwości `rEventProp` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`pomyślnie zwrócono.|  
|`S_FALSE`|Brak zdarzeń lub właściwości do wyliczenia. W takim przypadku `pcEventProp` jest równa zero.|  
  
## <a name="remarks"></a>Uwagi  
 Wiele typów środowiska uruchomieniowego języka wspólnego definiuje zdarzenia *Właściwości* `Changed` i `On` metody *Właściwości* `Changed` powiązane z ich właściwościami. Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> Typ definiuje <xref:System.Windows.Forms.Control.Font%2A> Właściwość, <xref:System.Windows.Forms.Control.FontChanged> zdarzenie i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodę. Metoda dostępu set metody <xref:System.Windows.Forms.Control.Font%2A> wywołania właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> , która z kolei podnosi <xref:System.Windows.Forms.Control.FontChanged> zdarzenie. Należy wywołać `EnumMethodSemantics` użycie elementu MethodDef dla, <xref:System.Windows.Forms.Control.OnFontChanged%2A> Aby uzyskać odwołania do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
