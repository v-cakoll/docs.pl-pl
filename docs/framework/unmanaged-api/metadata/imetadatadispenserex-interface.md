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
ms.openlocfilehash: 7d930088d6e621885d14fc4bdab2475aa27594e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserex-interface"></a>IMetaDataDispenserEx — Interfejs
Rozszerza [IMetaDataDispenser — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interfejsu możliwości, aby kontrolować sposób działania metadanych interfejsów API w bieżącym zakresie metadanych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindAssembly, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|Ta metoda nie jest zaimplementowana. Wywołuje się, zwraca E_NOTIMPL.|  
|[FindAssemblyModule, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|Ta metoda nie jest zaimplementowana. Wywołuje się, zwraca E_NOTIMPL.|  
|[GetCORSystemDirectory, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|Pobiera katalog, który zawiera bieżące środowisko uruchomieniowe języka wspólnego (CLR). Ta metoda jest obsługiwana tylko przez debugery poza procesem. Wywoływane z innego składnika, zwróci E_NOTIMPL.|  
|[GetOption, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.|  
|[OpenScopeOnITypeInfo, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|Ta metoda nie jest zaimplementowana. Wywołuje się, zwraca E_NOTIMPL.|  
|[SetOption, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|Ustawia określoną opcję do podanej wartości w bieżącym zakresie metadanych. Opcję określa sposób obsługi wywołania do bieżącego zakresu metadanych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
