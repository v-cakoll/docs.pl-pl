---
title: IMetaDataImport2 — Interfejs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429212"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 — Interfejs
Rozszerza interfejs [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) w celu zapewnienia możliwości pracy z typami ogólnymi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumGenericParamConstraints, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Pobiera moduł wyliczający dla tablicy ograniczeń parametrów ogólnych skojarzonych z parametrem ogólnym reprezentowanym przez określony token.|  
|[EnumGenericParams, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Pobiera moduł wyliczający dla tablicy tokenów parametrów ogólnych skojarzonych z określonym tokenem TypeDef lub MethodDef.|  
|[EnumMethodSpecs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Pobiera moduł wyliczający dla tablicy tokenów elementu MethodSpec skojarzonych z określonym tokenem MethodDef lub MemberRef.|  
|[GetGenericParamConstraintProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Pobiera metadane skojarzone z ograniczeniem parametru generycznego reprezentowane przez określony token ograniczenia.|  
|[GetGenericParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Pobiera metadane skojarzone z parametrem ogólnym reprezentowanym przez określony token.|  
|[GetMethodSpecProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Pobiera sygnaturę metadanych metody przywoływanej przez określony token elementu MethodSpec.|  
|[GetPEKind, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Pobiera wartość identyfikującą charakter kodu w przenośnym pliku wykonywalnym (PE), zazwyczaj plik DLL lub EXE, zdefiniowany w bieżącym zakresie metadanych|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Pobiera numer wersji środowiska uruchomieniowego, który został użyty do skompilowania zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
