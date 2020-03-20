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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178289"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult — Wyliczenie
Wskazuje równoważność dwóch tożsamości zestawu, zgodnie z funkcją [CompareAssemblyIdentity.](compareassemblyidentity-function.md)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`ACR_EquivalentFullMatch`|Wskazuje, że wszystkie pola zestawu w meczu porównania.|  
|`ACR_EquivalentFXUnified`|Wskazuje, że zestawy są uważane za równoważne na podstawie ujednolicenia wersji zestawu (CLR) common language runtime (Common Language Runtime Version) w programie .NET Framework w wersji 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Wskazuje częściowe dopasowanie zestawów na podstawie ujednolicenia CLR numerów wersji zestawu w programie .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Wskazuje częściowe dopasowanie zestawów.|  
|`ACR_EquivalentPartialUnified`|Wskazuje częściowe dopasowanie zestawów na podstawie starszego ujednolicenia numerów wersji.|  
|`ACR_EquivalentPartialWeakNamed`|Wskazuje częściowe dopasowanie po prostu nazwanych zestawów.|  
|`ACR_EquivalentUnified`|Wskazuje, że zestawy są uważane za równoważne na podstawie ujednolicenia CLR numerów wersji w starszych wersjach programu .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Wskazuje dopasowanie między dwoma po prostu nazwanych zestawów, których numery wersji zostały zignorowane.|  
|`ACR_NonEquivalent`|Wskazuje, że między dwoma zestawami nie doszło do dopasowania.|  
|`ACR_NonEquivalentPartialVersion`|Wskazuje, że dwa zestawy są zgodne z wyjątkiem ich numerów wersji, które pasują tylko częściowo.|  
|`ACR_NonEquivalentVersion`|Wskazuje, że dwa zestawy są zgodne z wyjątkiem ich numerów wersji, które nie są zgodne.|  
|`ACR_Unknown`|Wskazuje, że przyczyna braku równoważności nie jest znana.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fuzja.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [CompareAssemblyIdentity — Funkcja](compareassemblyidentity-function.md)
- [Wyliczenia łączenia](fusion-enumerations.md)
