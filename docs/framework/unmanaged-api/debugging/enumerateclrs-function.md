---
title: EnumerateCLRs — Funkcja
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 69288e995ec789091bf089368cd9a60f003df86e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122973"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs — Funkcja
Zapewnia mechanizm wyliczania CLRs w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 podczas Identyfikator procesu, z którego jest wyliczany załadowany CLRs.  
  
 `ppHandleArrayOut`  
 określoną Wskaźnik do tablicy zawierającej uchwyty zdarzeń, które są używane do kontynuowania uruchamiania CLR. Nie ma gwarancji, że każdy uchwyt w tablicy jest prawidłowy. Jeśli jest prawidłowy, dojście ma być używane jako zdarzenie kontynuacji dla odpowiedniego środowiska uruchomieniowego znajdujące się w tym samym indeksie `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 określoną Wskaźnik do tablicy ciągów, które określają pełne ścieżki do CLRs załadowane w procesie.  
  
 `pdwArrayLengthOut`  
 określoną Wskaźnik do typu DWORD, który zawiera długość równomiernie dopasowane `ppHandleArrayOut` i `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 `ppHandleArrayOut` lub `ppStringArrayOut` ma wartość null lub `pdwArrayLengthOut` ma wartość null.  
  
 E_OUTOFMEMORY  
 Funkcja nie może przydzielić wystarczającej ilości pamięci dla tablic uchwytu i ścieżki.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można wyliczyć załadowanych CLRs.  
  
## <a name="remarks"></a>Uwagi  
 Dla procesu docelowego, który jest identyfikowany przez `debuggeePID`, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`, aby CLRs załadować w procesie; Tablica dojść do zdarzeń, `ppHandleArrayOut`, która może zawierać zdarzenie kontynuacji uruchamiania dla środowiska CLR w tym samym indeksie; i rozmiar tablic, `pdwArrayLengthOut`, który określa liczbę załadowanych CLRs.  
  
 W systemie operacyjnym Windows `debuggeePID` mapuje na identyfikator procesu systemu operacyjnego.  
  
 Pamięć dla `ppHandleArrayOut` i `ppStringArrayOut` są przydzielone przez tę funkcję. Aby zwolnić przydzieloną pamięć, należy wywołać [funkcję CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Tę funkcję można wywołać z parametrami tablicy ustawionymi na wartość null, aby można było zwrócić liczbę CLRs w procesie docelowym. Z tego licznika obiekt wywołujący może wnioskować o rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim. h  
  
 **Biblioteka:** dbgshim. dll  
  
 **.NET Framework wersje:** 3,5 SP1
