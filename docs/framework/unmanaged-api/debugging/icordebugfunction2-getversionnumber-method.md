---
title: ICorDebugFunction2::GetVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497174"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber — Metoda
Pobiera Edytuj i Kontynuuj wersja tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnVersion`  
 [out] Wskaźnik do liczby całkowitej, który jest numer wersji funkcji, który jest reprezentowany przez ten obiekt icordebugfunction2 —.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe przechowuje informacje o liczbę zmian, które miały miejsce do poszczególnych modułów podczas sesji debugowania. Numer wersji funkcji jest jednym więcej niż liczba edycji, który wprowadzono funkcję. Oryginalna wersja funkcji jest w wersji 1. Numer jest zwiększany dla modułu, każdym razem, gdy [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) jest wywoływana w module. W związku z tym jeśli treść funkcji został zastąpiony w wywołaniu pierwszy i trzeci `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` może zwrócić wersję 1, 2 lub 4 dla tej funkcji, ale nie w wersji 3. (Ta funkcja będzie miała wersji 3).  
  
 Numer wersji jest śledzone oddzielnie dla każdego modułu. Tak Jeśli cztery edycje na Module 1 i brak na Module 2, dalej zmiany w Module 1 przypisze numeru wersji 6 wszystkie funkcje edytowanych w Module 1. Jeśli moduł 2 ma takie same edytować, funkcje w Module 2 zostanie wyświetlony numer wersji 2.  
  
 Numer wersji uzyskanych przez `GetVersionNumber` metoda może być mniejszy niż uzyskanych przez [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda wykonuje tej samej operacji co `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
