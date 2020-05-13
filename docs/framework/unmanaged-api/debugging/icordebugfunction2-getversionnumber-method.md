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
ms.openlocfilehash: f47263872b1baf1038a5fa9816c96e3e2569e705
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213221"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber — Metoda
Pobiera wersję Edytuj i Kontynuuj tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnVersion`  
 określoną Wskaźnik do liczby całkowitej, która jest numerem wersji funkcji reprezentowanej przez ten obiekt ICorDebugFunction2.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe śledzi liczbę zmian, które zostały zastosowane do każdego modułu podczas sesji debugowania. Numer wersji funkcji jest jeden więcej niż liczba edycji, która wprowadziła funkcję. Oryginalna wersja funkcji to wersja 1. Liczba jest zwiększana dla modułu za każdym razem, gdy [ICorDebugModule2:: ApplyChanges —](icordebugmodule2-applychanges-method.md) jest wywoływana dla tego modułu. Tak więc, jeśli treść funkcji została zamieniona na pierwsze i trzecie wywołanie do `ICorDebugModule2::ApplyChanges` , `GetVersionNumber` może zwrócić wersję 1, 2 lub 4 dla tej funkcji, ale nie w wersji 3. (Ta funkcja nie ma wersji 3).  
  
 Numer wersji jest śledzony oddzielnie dla każdego modułu. Dlatego w przypadku przeprowadzenia czterech zmian w module 1 i braku w module 2 kolejna edycja w module 1 przypisze numer wersji 6 do wszystkich edytowanych funkcji w module 1. Jeśli ta sama Edycja obejmuje moduł 2, funkcje w module 2 uzyskają numer wersji 2.  
  
 Numer wersji uzyskany przez `GetVersionNumber` metodę może być niższy niż uzyskany przez [ICorDebugFunction:: GetCurrentVersionNumber —](icordebugfunction-getcurrentversionnumber-method.md).  
  
 Metoda [ICorDebugCode:: GetVersionNumber —](icordebugcode-getversionnumber-method.md) wykonuje tę samą operację co `ICorDebugFunction2::GetVersionNumber` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
