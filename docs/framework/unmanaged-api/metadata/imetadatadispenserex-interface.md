---
title: "IMetaDataDispenserEx — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
