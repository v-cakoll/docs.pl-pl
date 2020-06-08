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
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490399"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 — Interfejs
Rozszerza interfejs [IMetaDataImport](imetadataimport-interface.md) w celu zapewnienia możliwości pracy z typami ogólnymi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumGenericParamConstraints — Metoda](imetadataimport2-enumgenericparamconstraints-method.md)|Pobiera moduł wyliczający dla tablicy ograniczeń parametrów ogólnych skojarzonych z parametrem ogólnym reprezentowanym przez określony token.|  
|[EnumGenericParams — Metoda](imetadataimport2-enumgenericparams-method.md)|Pobiera moduł wyliczający dla tablicy tokenów parametrów ogólnych skojarzonych z określonym tokenem TypeDef lub MethodDef.|  
|[EnumMethodSpecs — Metoda](imetadataimport2-enummethodspecs-method.md)|Pobiera moduł wyliczający dla tablicy tokenów elementu MethodSpec skojarzonych z określonym tokenem MethodDef lub MemberRef.|  
|[GetGenericParamConstraintProps — Metoda](imetadataimport2-getgenericparamconstraintprops-method.md)|Pobiera metadane skojarzone z ograniczeniem parametru generycznego reprezentowane przez określony token ograniczenia.|  
|[GetGenericParamProps — Metoda](imetadataimport2-getgenericparamprops-method.md)|Pobiera metadane skojarzone z parametrem ogólnym reprezentowanym przez określony token.|  
|[GetMethodSpecProps — Metoda](imetadataimport2-getmethodspecprops-method.md)|Pobiera sygnaturę metadanych metody przywoływanej przez określony token elementu MethodSpec.|  
|[GetPEKind — Metoda](imetadataimport2-getpekind-method.md)|Pobiera wartość identyfikującą charakter kodu w przenośnym pliku wykonywalnym (PE), zazwyczaj plik DLL lub EXE, zdefiniowany w bieżącym zakresie metadanych|  
|[GetVersionString — Metoda](imetadataimport2-getversionstring-method.md)|Pobiera numer wersji środowiska uruchomieniowego, który został użyty do skompilowania zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfejsy metadanych](metadata-interfaces.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
