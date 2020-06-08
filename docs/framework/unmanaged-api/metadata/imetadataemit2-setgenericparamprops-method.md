---
title: IMetaDataEmit2::SetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492740"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps — Metoda
Ustawia wartości właściwości dla definicji parametru generycznego, do której odwołuje się określony token.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `gp`  
 podczas Token dla definicji parametru generycznego, dla którego mają zostać ustawione wartości.  
  
 `dwParamFlags`  
 podczas Wartość wyliczenia [CorGenericParamAttr —](corgenericparamattr-enumeration.md) opisująca typ parametru generycznego.  
  
 `szName`  
 podczas Obowiązkowe. Nazwa parametru, dla którego mają zostać ustawione wartości.  
  
 `reserved`  
 podczas Zarezerwowane do użytku w przyszłości.  
  
 `rtkConstraints`  
 podczas Obowiązkowe. Tablica zakończona zerem z ograniczeniami typu. Elementy członkowskie tablicy muszą być `mdTypeDef` `mdTypeRef` `mdTypeSpec` tokenami, lub.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
