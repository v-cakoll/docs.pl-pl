---
title: CompareAssemblyIdentity — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 652000367c19572f73296c704047830ce1c74574
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914527"
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
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyIdentity1`  
 [in] Tożsamość tekstową pierwszego zestawu do porównania.  
  
 `fUnified1`  
 [in] Flagę logiczną, wskazującą, określonych przez użytkownika ujednolicenie dla `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 [in] Tożsamość tekstową drugiego zestawu do porównania.  
  
 `fUnified2`  
 [in] Flagę logiczną, wskazującą, określonych przez użytkownika ujednolicenie dla `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 [out] Flaga wartości logicznej, która wskazuje, czy dwa zestawy są równoważne.  
  
 `pResult`  
 [out] [Assemblycomparisonresult —](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md) wyliczenie, które zawiera szczegółowe informacje na temat porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `pfEquivalent` Zwraca wartość logiczną wskazującą, czy dwa zestawy są równoważne. `pResult` Zwraca jedną z `AssemblyComparisonResult` wartości, aby zapewnić bardziej szczegółowe Przyczyna wartość `pfEquivalent`.  
  
## <a name="remarks"></a>Uwagi  
 `CompareAssemblyIdentity` sprawdza, czy `pwzAssemblyIdentity1` i `pwzAssemblyIdentity2` są równoważne. `pfEquivalent` ustawiono `true` w jednej lub więcej z następujących warunków:  
  
- Tożsamości dwóch zestawów są równoważne. Dla zestawów o silnej nazwie równoważności wymaga nazwy zestawu, wersji, token klucza publicznego i kultury być identyczne. Po prostu nazwane zestawy równoważności wymaga dopasowania nazwy zestawu i kultury.  
  
- Zarówno tożsamości zestawu odnoszą się do zestawów, korzystających z programu .NET Framework. Zwraca ten warunek `true` nawet wtedy, gdy numery wersji zestawu nie są zgodne.  
  
- Dwa zestawy nie są zarządzane zestawy, ale `fUnified1` lub `fUnified2` została ustawiona na `true`.  
  
 `fUnified` Flaga wskazuje, że wszystkie numery wersji do numeru wersji zestawu o silnej nazwie są uważane za równoważne do zestawu o silnej nazwie. Na przykład jeśli wartość `pwzAssemblyIndentity1` jest "MyAssembly, wersji = 3.0.0.0, culture = neutral, publicKeyToken =..." i wartość `fUnified1` jest `true`, oznacza to, że wszystkie wersje MyAssembly z wersji 0.0.0.0 do 3.0.0.0 powinny być traktowane jako równoważne. W takim przypadku jeśli `pwzAssemblyIndentity2` odwołuje się do tego samego zestawu co `pwzAssemblyIndentity1`, z tą różnicą, że ma niższy numer wersji `pfEquivalent` jest równa `true`. Jeśli `pwzAssemblyIdentity2` odwołuje się do wyższy numer wersji `pfEquivalent` ustawiono `true` tylko wtedy, gdy wartość `fUnified2` jest `true`.  
  
 `pResult` Parametr zawiera szczegółowe informacje na temat przyczyny dwa zestawy są uważane za równoważne lub nie jest równorzędny. Aby uzyskać więcej informacji, zobacz [assemblycomparisonresult — wyliczenie](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [AssemblyComparisonResult, wyliczenie](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
