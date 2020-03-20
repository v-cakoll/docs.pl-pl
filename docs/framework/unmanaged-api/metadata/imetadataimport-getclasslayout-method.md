---
title: IMetaDataImport::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175411"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout — Metoda
Pobiera informacje o układzie dla klasy, do którego odwołuje się określony token TypeDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [w] TypeDef token dla klasy z układu do zwrócenia.  
  
 `pdwPackSize`  
 [na zewnątrz] Jedna z wartości 1, 2, 4, 8 lub 16, reprezentująca rozmiar opakowania klasy.  
  
 `rFieldOffset`  
 [na zewnątrz] Tablica [wartości COR_FIELD_OFFSET.](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)  
  
 `cMax`  
 [w] Maksymalny rozmiar `rFieldOffset` tablicy.  
  
 `pcFieldOffset`  
 [na zewnątrz] Liczba elementów zwróconych w `rFieldOffset`programie .  
  
 `pulClassSize`  
 [na zewnątrz] Rozmiar w bajtach klasy reprezentowanej przez `td`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
