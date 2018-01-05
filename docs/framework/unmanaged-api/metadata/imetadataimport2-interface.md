---
title: "IMetaDataImport2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7cd9d2cd2837ff43fbb266717546db3aa98190e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 — Interfejs
Rozszerza [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu możliwości pracy z typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumGenericParamConstraints, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego reprezentowany przez określony token.|  
|[EnumGenericParams, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Pobiera moduł wyliczający dla tablicy parametrów ogólnych tokenów skojarzone z określonym TypeDef lub MethodDef token.|  
|[EnumMethodSpecs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef token.|  
|[GetGenericParamConstraintProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Pobiera metadane skojarzone z ograniczenia parametru ogólnego reprezentowany przez ograniczenie określony token.|  
|[GetGenericParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Pobiera metadane skojarzone z parametru ogólnego reprezentowany przez określony token.|  
|[GetMethodSpecProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Pobiera token podpisu metadanych metody odwołuje się określony element MethodSpec.|  
|[GetPEKind, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Pobiera wartość identyfikujący rodzaj kod przenośny plik wykonywalny (PE) pliku, zwykle plik DLL ani EXE, zdefiniowany w bieżącym zakresie metadanych|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Pobiera numer wersji środowiska uruchomieniowego, który został użyty do budowania zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.PortableExecutableKinds>  
 [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
