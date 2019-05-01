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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777705"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics — Metoda
Pobiera flagi wskazującą związek między odwołuje się określony token MethodDef oraz sparowany właściwości, metody i zdarzenia odwołuje się określona EventProp token.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token MethodDef reprezentujący metodę, które mają być pobrane informacje semantyczne roli.  
  
 `tkEventProp`  
 [in] Token reprezentujący par właściwości i zdarzenia, dla którego należy pobrać rolę metody.  
  
 `pdwSemanticsFlags`  
 [out] Wskaźnik flagi skojarzone semantyki. Ta wartość jest z [cormethodsemanticsattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metody Ustawia flagi semantyki metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
