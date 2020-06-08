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
ms.openlocfilehash: 7a2a5080872f49a84e36c53ac337d91738c15e45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501342"
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter — Interfejs
Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo — Metoda](imetadataconverter-getmetadatafromtypeinfo-method.md)|Pobiera wskaźnik do wystąpienia [IMetaDataImport](imetadataimport-interface.md) , które reprezentuje sygnaturę metadanych dla biblioteki typów, do której odwołuje się określone `ITypeInfo` wystąpienie.|  
|[GetMetaDataFromTypeLib — Metoda](imetadataconverter-getmetadatafromtypelib-method.md)|Pobiera wskaźnik do `IMetaDataImport` wystąpienia, które reprezentuje sygnaturę metadanych dla biblioteki typów reprezentowanej przez określone `ITypeLib` wystąpienie.|  
|[GetTypeLibFromMetaData — Metoda](imetadataconverter-gettypelibfrommetadata-method.md)|Pobiera wskaźnik do `ITypeLib` wystąpienia, które reprezentuje bibliotekę typów, która ma określone nazwy modułów i bibliotek.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
