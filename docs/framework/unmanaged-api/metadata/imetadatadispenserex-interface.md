---
title: IMetaDataDispenserEx — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96475086b1244ae75ed692dd10cb693af0be9af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992605"
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx — Interfejs
Rozszerza [imetadatadispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interfejsu, aby zapewnić możliwość kontrolowania, jak działają metadanych interfejsów API w bieżącym zakresie metadanych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindAssembly, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Ta metoda nie jest zaimplementowana. Jeżeli jest wywoływana, zwraca E_NOTIMPL.|  
|[FindAssemblyModule, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Ta metoda nie jest zaimplementowana. Jeżeli jest wywoływana, zwraca E_NOTIMPL.|  
|[GetCORSystemDirectory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR). Ta metoda jest obsługiwana tylko do użytku przez debugery spoza procesu. Wywoływana z innego składnika, zwróci E_NOTIMPL.|  
|[GetOption, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.|  
|[OpenScopeOnITypeInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Ta metoda nie jest zaimplementowana. Jeżeli jest wywoływana, zwraca E_NOTIMPL.|  
|[SetOption, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych. Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
