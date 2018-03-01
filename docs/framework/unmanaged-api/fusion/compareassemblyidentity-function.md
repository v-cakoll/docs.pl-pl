---
title: "CompareAssemblyIdentity — Funkcja"
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
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 266868a65a0db75b57d46d92a469b4b6ceaa88e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity — Funkcja
Porównuje dwa tożsamości zestawu do ustalenia, czy są równoważne.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzAssemblyIdentity1`  
 [in] Tożsamości tekstowej pierwszego zestawu do porównania.  
  
 `fUnified1`  
 [in] Wartość logiczna flagę wskazującą, ujednolicenie określone przez użytkownika dla `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Tożsamość tekstową drugiego zestawu do porównania.  
  
 `fUnified2`  
 [in] Wartość logiczna flagę wskazującą, ujednolicenie określone przez użytkownika dla `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Flaga wartości logicznej, która wskazuje, czy dwa zestawy są równoważne.  
  
 `pResult`  
 [out] [AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) wyliczenia, który zawiera szczegółowe informacje dotyczące porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `pfEquivalent`Zwraca wartość logiczną, wskazującą, czy dwa zestawy są równoważne. `pResult`Zwraca jedną z `AssemblyComparisonResult` wartości, aby nadać bardziej szczegółowe Przyczyna wartość `pfEquivalent`.  
  
## <a name="remarks"></a>Uwagi  
 `CompareAssemblyIdentity`sprawdza, czy `pwzAssemblyIdentity1` i `pwzAssemblyIdentity2` są równoważne. `pfEquivalent`ustawiono `true` w jednej lub więcej z następujących warunków:  
  
-   Tożsamości dwóch zestawów są równoważne. Dla zestawów o silnej nazwie równoważność wymaga nazwy zestawu, wersję, token klucza publicznego i kultury, aby była taka sama. W przypadku po prostu nazwane zestawy równoważność wymaga pasującego do nazwy zestawu i kultury.  
  
-   Zarówno tożsamości zestawu odwołuje się do zestawów, które są uruchamiane w programie .NET Framework. Ten warunek zwraca `true` nawet wtedy, gdy numery wersji zestawu nie są zgodne.  
  
-   Dwa zestawy nie są zarządzane zestawy, ale `fUnified1` lub `fUnified2` ustawiono `true`.  
  
 `fUnified` Flaga wskazuje, że wszystkie numery wersji do wersji liczby zestawu o silnej nazwie zostały uznane za równorzędne do zestawu o silnej nazwie. Na przykład jeśli wartość `pwzAssemblyIndentity1` jest "MyAssembly, wersja 3.0.0.0, culture = neutral, publicKeyToken = =..." i wartość `fUnified1` jest `true`, oznacza to, że wszystkie wersje MyAssembly z wersji 0.0.0.0 i 3.0.0.0 powinny być traktowane jako równoważne. W takim przypadku jeśli `pwzAssemblyIndentity2` odwołuje się do tego samego zestawu jako `pwzAssemblyIndentity1`, z wyjątkiem tego, że ma ona na niższą wersję `pfEquivalent` ma ustawioną wartość `true`. Jeśli `pwzAssemblyIdentity2` odwołuje się do wyższy numer wersji, `pfEquivalent` ustawiono `true` tylko wtedy, gdy wartość `fUnified2` jest `true`.  
  
 `pResult` Parametr zawiera szczegółowe informacje na temat przyczyny dwa zestawy są traktowane jako równoważne lub nie jest równorzędny. Aby uzyskać więcej informacji, zobacz [AssemblyComparisonResult — wyliczenie](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult, wyliczenie](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
