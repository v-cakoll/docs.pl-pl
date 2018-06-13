---
title: AssemblyComparisonResult — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82b81ec29dece182548ead046edc7cb754fbf00e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430664"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult — Wyliczenie
Wskazuje równoważność tożsamości dwóch zestawów, zgodnie z ustaleniami [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Wskazuje, że zestaw wszystkich pól w dopasowania porównania.|  
|`ACR_EquivalentFXUnified`|Wskazuje, że zestawy zostały uznane za równorzędne oparte na wspólnej ujednolicenie środowiska uruchomieniowego języka wersji (języka wspólnego CLR) numerów wersji zestawu w programie .NET Framework w wersji 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Wskazuje częściowe dopasowanie zestawów, w oparciu o ujednolicenie CLR numerów wersji zestawu w .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Wskazuje częściowe dopasowanie zestawów.|  
|`ACR_EquivalentPartialUnified`|Wskazuje częściowe dopasowanie zestawów, w oparciu o starszych ujednolicenie numerów wersji.|  
|`ACR_EquivalentPartialWeakNamed`|Wskazuje częściowe dopasowanie po prostu nazwane zestawy.|  
|`ACR_EquivalentUnified`|Wskazuje, że zestawy zostały uznane za równorzędne oparte na ujednolicenie CLR numerów wersji w starszych wersjach programu .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Wskazuje zgodność między dwa po prostu nazwane zestawy, których numery wersji zostały zignorowane.|  
|`ACR_NonEquivalent`|Wskazuje, czy nie wystąpił między dwoma zestawami.|  
|`ACR_NonEquivalentPartialVersion`|Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji tylko częściowo zgodne.|  
|`ACR_NonEquivalentVersion`|Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji, które nie są zgodne.|  
|`ACR_Unknown`|Wskazuje, przyczyna nie when jest nieznana.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CompareAssemblyIdentity, funkcja](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
