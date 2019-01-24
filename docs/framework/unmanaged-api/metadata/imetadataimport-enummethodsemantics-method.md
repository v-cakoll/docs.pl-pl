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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c20e2787eb8071b10e06b980572c347959fe3c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619451"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics — Metoda
Wylicza właściwości i zdarzenia zmiany właściwości, do których odnosi się określonej metody.  
  
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
 [out w] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwszego wywołania tej metody.  
  
 `mb`  
 [in] Token MethodDef, który ogranicza zakres wyliczenia.  
  
 `rEventProp`  
 [out] Tablica do przechowywania właściwości lub zdarzenia.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rEventProp` tablicy.  
  
 `pcEventProp`  
 [out] Numer zdarzenia lub właściwości zwracane w `rEventProp`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` pomyślnie zwrócił.|  
|`S_FALSE`|Brak zdarzeń i właściwości do wyliczenia. W takim przypadku `pcEventProp` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Zdefiniuj wiele typów środowiska wykonawczego języka wspólnego *właściwość* `Changed` zdarzeń i `On` *właściwość* `Changed` metody odnoszące się do ich właściwości. Na przykład <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definiuje <xref:System.Windows.Forms.Control.Font%2A> właściwości <xref:System.Windows.Forms.Control.FontChanged> zdarzenia i <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody. Metoda dostępu set <xref:System.Windows.Forms.Control.Font%2A> wywołaniach właściwości <xref:System.Windows.Forms.Control.OnFontChanged%2A> metody, która z kolei wywołuje <xref:System.Windows.Forms.Control.FontChanged> zdarzeń. Możesz wywołać `EnumMethodSemantics` przy użyciu MethodDef dla <xref:System.Windows.Forms.Control.OnFontChanged%2A> uzyskać odwołania do <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.Control.FontChanged> zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
