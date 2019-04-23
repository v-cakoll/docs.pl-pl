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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211936"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 — Interfejs
Rozszerza [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu, aby zapewnić możliwość pracy z typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumGenericParamConstraints, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Pobiera moduł wyliczający dla tablicy ograniczenia parametru ogólnego skojarzone z parametru ogólnego, reprezentowane przez określony token.|  
|[EnumGenericParams, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Pobiera moduł wyliczający dla tablic, tokeny parametrów ogólnych skojarzone z określonego typu lub MethodDef token.|  
|[EnumMethodSpecs, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Pobiera moduł wyliczający dla tablicy tokenów MethodSpec skojarzone z określonym MethodDef lub MemberRef tokenu.|  
|[GetGenericParamConstraintProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.|  
|[GetGenericParamProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.|  
|[GetMethodSpecProps, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Sygnatura metadanych metody odwołuje się określona MethodSpec pobiera token.|  
|[GetPEKind, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Pobiera wartość identyfikujący rodzaj kodu w przenośnym pliku wykonywalnym (PE) pliku, zazwyczaj pliku DLL lub EXE, zdefiniowana w bieżącym zakresie metadanych|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Pobiera numer wersji środowiska uruchomieniowego, który został użyty do tworzenia zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.PortableExecutableKinds>
- [Interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
