---
title: IMetaDataAssemblyImport::EnumManifestResources — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176022"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>IMetaDataAssemblyImport::EnumManifestResources — Metoda
Pobiera wskaźnik do wyliczania zasobów, do których odwołuje się w bieżącym manifeście zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, na zewnątrz] Wskaźnik do wyliczacza. Musi to być wartość `EnumManifestResources` null, gdy metoda jest wywoływana po raz pierwszy.  
  
 `rManifestResources`  
 [na zewnątrz] Tablica używana do `mdManifestResource` przechowywania tokenów metadanych.  
  
 `cMax`  
 [w] Maksymalna liczba `mdManifestResource` tokenów, które `rManifestResources`można umieścić w .  
  
 `pcTokens`  
 [na zewnątrz] Liczba tokenów `mdManifestResource` faktycznie umieszczonych w `rManifestResources`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim `pcTokens` przypadku jest ustawiona na zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
