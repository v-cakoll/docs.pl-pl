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
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437450"
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
 określoną Wskaźnik do skojarzonych flag semantycznych. Ta wartość jest maska bitowa z wyliczenia [CorMethodSemanticsAttr —](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 [IMetaDataEmit::D efineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) Metoda ustawia flagi semantyki metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
