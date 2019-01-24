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
ms.openlocfilehash: 1b844a660da6a1e8d96ed7f5833435b413219e29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645629"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult — Wyliczenie
Wskazuje na równoważność dwóch tożsamości zestawu, zgodnie z ustaleniami [compareassemblyidentity —](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkcji.  
  
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
|`ACR_EquivalentFullMatch`|Wskazuje, że zestaw wszystkich pól dopasowania porównania.|  
|`ACR_EquivalentFXUnified`|Wskazuje, że zestawy są uważane za równoważne oparte na wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji ujednolicenie numery wersji zestawu w .NET Framework w wersji 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Wskazuje częściowe dopasowanie zestawów, w oparciu o ujednolicenie środowiska CLR numery wersji zestawu w programie .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Wskazuje częściowe dopasowanie zestawów.|  
|`ACR_EquivalentPartialUnified`|Wskazuje częściowym zestawy oparte na starszych ujednolicenie numerów wersji.|  
|`ACR_EquivalentPartialWeakNamed`|Wskazuje częściowe dopasowanie, po prostu nazwanych zestawów.|  
|`ACR_EquivalentUnified`|Wskazuje, że zestawy są uważane za równoważne oparte na ujednolicenie środowiska CLR numery wersji w starszych wersjach programu .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Wskazuje zgodność między dwa po prostu nazwane zestawy, których numery wersji zostały zignorowane.|  
|`ACR_NonEquivalent`|Wskazuje, że dopasowanie nie wystąpił między dwoma zestawami.|  
|`ACR_NonEquivalentPartialVersion`|Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji i tylko częściowo zgodne.|  
|`ACR_NonEquivalentVersion`|Wskazuje, że te dwa zestawy są zgodne z wyjątkiem ich numery wersji, które nie są zgodne.|  
|`ACR_Unknown`|Wskazuje przyczynę niż równoważności jest nieznany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [CompareAssemblyIdentity, funkcja](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
