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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0c9f104329818f47597e8735389e5e6205ca617
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777104"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps — Metoda
Ustawia wartości właściwości dla definicji parametru ogólnego odwołuje się określony token.  
  
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
 [in] Token dla definicji parametru ogólnego, dla którego mają zostać ustawione wartości.  
  
 `dwParamFlags`  
 [in] Wartość [corgenericparamattr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące typ dla parametru ogólnego.  
  
 `szName`  
 [in] Opcjonalnie. Nazwa parametru, do których chcesz ustawić wartości.  
  
 `reserved`  
 [in] Zarezerwowane dla przyszłej rozszerzalności.  
  
 `rtkConstraints`  
 [in] Opcjonalnie. Tablica zakończony zerem ograniczenia typu. Elementy członkowskie tablicy musi być `mdTypeDef`, `mdTypeRef`, lub `mdTypeSpec` token metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
