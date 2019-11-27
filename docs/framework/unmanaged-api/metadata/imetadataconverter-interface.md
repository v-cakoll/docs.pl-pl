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
ms.openlocfilehash: b771b368c069a4577d266b47bfb4a5ee1935e48e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436272"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter — Interfejs
Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Pobiera wskaźnik do wystąpienia [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych dla biblioteki typów, do której odwołuje się określone wystąpienie `ITypeInfo`.|  
|[GetMetaDataFromTypeLib, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|Pobiera wskaźnik do wystąpienia `IMetaDataImport`, które reprezentuje podpis metadanych dla biblioteki typów reprezentowanej przez określone wystąpienie `ITypeLib`.|  
|[GetTypeLibFromMetaData, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|Pobiera wskaźnik do wystąpienia `ITypeLib`, które reprezentuje bibliotekę typów, która zawiera określone nazwy modułów i bibliotek.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
