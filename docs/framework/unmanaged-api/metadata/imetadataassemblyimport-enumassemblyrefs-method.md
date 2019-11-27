---
title: IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450349"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a>IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda
Wylicza `mdAssemblyRef` wystąpienia, które są zdefiniowane w manifeście zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in. out] Wskaźnik do modułu wyliczającego. Ta wartość musi być wartością null, gdy metoda `EnumAssemblyRefs` jest wywoływana po raz pierwszy.  
  
 `rAssemblyRefs`  
 określoną Wyliczanie tokenów metadanych `mdAssemblyRef`.  
  
 `cMax`  
 podczas Maksymalna liczba tokenów, które mogą być umieszczone w tablicy `rAssemblyRefs`.  
  
 `pcTokens`  
 określoną Liczba tokenów faktycznie umieszczonych w `rAssemblyRefs`.  
  
## <a name="return-value"></a>Wartość zwrócona  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumAssemblyRefs` pomyślnie zwrócone.|  
|`S_FALSE`|Brak tokenów do wyliczenia. W tym przypadku `pcTokens` jest ustawiona na zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
