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
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450078"
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
 podczas Maksymalny rozmiar tablicy `rEventProp`.  
  
 `pcEventProp`  
 określoną Liczba zdarzeń lub właściwości zwróconych w `rEventProp`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` pomyślnie zwrócone.|  
|`S_FALSE`|Brak zdarzeń lub właściwości do wyliczenia. W takim przypadku `pcEventProp` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Wiele typów środowiska uruchomieniowego języka *wspólnego definiuje`Changed`* zdarzeń i *Właściwości* `On``Changed` metod związanych z ich właściwościami. Na przykład typ <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definiuje Właściwość <xref:System.Windows.Forms.Control.Font%2A>, zdarzenie <xref:System.Windows.Forms.Control.FontChanged> i metodę <xref:System.Windows.Forms.Control.OnFontChanged%2A>. Metoda metody dostępu set właściwości <xref:System.Windows.Forms.Control.Font%2A> wywołuje metodę <xref:System.Windows.Forms.Control.OnFontChanged%2A>, która z kolei podnosi zdarzenie <xref:System.Windows.Forms.Control.FontChanged>. Należy wywołać `EnumMethodSemantics` przy użyciu elementu MethodDef dla <xref:System.Windows.Forms.Control.OnFontChanged%2A>, aby uzyskać odwołania do właściwości <xref:System.Windows.Forms.Control.Font%2A> i zdarzenia <xref:System.Windows.Forms.Control.FontChanged>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
