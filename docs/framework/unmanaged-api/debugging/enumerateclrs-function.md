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
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860727"
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
 określoną Wskaźnik do tablicy zawierającej uchwyty zdarzeń, które są używane do kontynuowania uruchamiania CLR. Nie ma gwarancji, że każdy uchwyt w tablicy jest prawidłowy. Jeśli jest prawidłowy, dojście ma być używane jako zdarzenie kontynuacji uruchamiania dla odpowiedniego środowiska uruchomieniowego, które znajduje się w tym `ppStringArrayOut`samym indeksie.  
  
 `ppStringArrayOut`  
 określoną Wskaźnik do tablicy ciągów, które określają pełne ścieżki do CLRs załadowane w procesie.  
  
 `pdwArrayLengthOut`  
 określoną Wskaźnik na wartość typu DWORD, która zawiera długość równomiernie `ppHandleArrayOut` dopasowanego `pdwArrayLengthOut`rozmiaru i.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 Albo ma wartość null lub `pdwArrayLengthOut` ma wartość null. `ppHandleArrayOut` `ppStringArrayOut`  
  
 E_OUTOFMEMORY  
 Funkcja nie może przydzielić wystarczającej ilości pamięci dla tablic uchwytu i ścieżki.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można wyliczyć załadowanych CLRs.  
  
## <a name="remarks"></a>Uwagi  
 Dla procesu docelowego, który jest identyfikowany `debuggeePID`przez, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`do CLRs załadowane w procesie; Tablica dojść do zdarzeń, `ppHandleArrayOut`która może zawierać zdarzenie kontynuacji uruchamiania dla środowiska CLR w tym samym indeksie; i wielkość tablic `pdwArrayLengthOut`, która określa liczbę CLRs ładowanych.  
  
 W systemie operacyjnym Windows `debuggeePID` mapuje na identyfikator procesu systemu operacyjnego.  
  
 Pamięć dla `ppHandleArrayOut` i `ppStringArrayOut` są przydzielone przez tę funkcję. Aby zwolnić przydzieloną pamięć, należy wywołać [funkcję CloseCLREnumeration](closeclrenumeration-function.md).  
  
 Tę funkcję można wywołać z parametrami tablicy ustawionymi na wartość null, aby można było zwrócić liczbę CLRs w procesie docelowym. Z tego licznika obiekt wywołujący może wnioskować o rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim. h  
  
 **Biblioteka:** dbgshim. dll  
  
 **.NET Framework wersje:** 3,5 SP1
