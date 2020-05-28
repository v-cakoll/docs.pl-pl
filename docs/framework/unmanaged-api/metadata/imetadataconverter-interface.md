---
title: IMetaDataConverter — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: b6ca7c619d32e69ffac20b80561171d0320db2d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008381"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter — Interfejs
Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo — Metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Pobiera wskaźnik do wystąpienia [IMetaDataImport](imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych dla biblioteki typów, do której odwołuje się określone `ITypeInfo` wystąpienie.|  
|[GetMetaDataFromTypeLib — Metoda](imetadataconverter-getmetadatafromtypelib-method.md)|Pobiera wskaźnik do `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych dla biblioteki typów reprezentowanej przez określone `ITypeLib` wystąpienie.|  
|[GetTypeLibFromMetaData — Metoda](imetadataconverter-gettypelibfrommetadata-method.md)|Pobiera wskaźnik do `ITypeLib` wystąpienia, które reprezentuje bibliotekę typów, która ma określone nazwy modułów i bibliotek.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
