---
title: IMetaDataImport::GetMethodSemantics — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 2cfb66203d8f2d69ea188f6913a5ef34dd74791e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503604"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics — Metoda
Pobiera flagi wskazujące relację między metodą przywoływaną przez określony token MethodDef i sparowaną właściwością i zdarzeniem, do którego odwołuje się określony token EventProp.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 podczas Token MethodDef reprezentujący metodę uzyskiwania informacji o roli semantycznej dla.  
  
 `tkEventProp`  
 podczas Token reprezentujący sparowaną Właściwość i zdarzenie, dla którego ma zostać uzyskana rola metody.  
  
 `pdwSemanticsFlags`  
 określoną Wskaźnik do skojarzonych flag semantycznych. Ta wartość jest maska bitowa z wyliczenia [CorMethodSemanticsAttr —](cormethodsemanticsattr-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 [IMetaDataEmit::D efineproperty](imetadataemit-defineproperty-method.md) Metoda ustawia flagi semantyki metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
