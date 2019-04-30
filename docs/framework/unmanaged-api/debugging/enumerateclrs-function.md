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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698216"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs — Funkcja
Udostępnia mechanizm wyliczania CLRs w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [in] Proces identyfikator procesu, z którego będzie można wyliczyć CLRs załadowane.  
  
 `ppHandleArrayOut`  
 [out] Wskaźnik na tablicę zawierającą dojścia zdarzenia, które są używane w dalszym uruchamiania aparatu CLR. Dojście do każdego w tablicy nie jest gwarantowana był prawidłowy. Jeśli prawidłowy, uchwyt ma być używany jako zdarzenie Kontynuuj uruchamiania dla odpowiedniego środowiska uruchomieniowego, znajduje się w tym samym indeksie `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Wskaźnik na tablicę ciągów, które określają pełnej ścieżki do CLRs załadowany w procesie.  
  
 `pdwArrayLengthOut`  
 [out] Wskaźnik do typu DWORD, który zawiera długości równej wielkości `ppHandleArrayOut` i `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 Albo `ppHandleArrayOut` lub `ppStringArrayOut` ma wartość null, lub `pdwArrayLengthOut` ma wartość null.  
  
 E_OUTOFMEMORY  
 Funkcja nie może przydzielić wystarczającej ilości pamięci dla tablic dojścia i ścieżkę.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można wyliczyć CLRs załadowane.  
  
## <a name="remarks"></a>Uwagi  
 Dla procesu docelowego, który jest identyfikowany przez `debuggeePID`, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`, CLRs załadowany w procesie; tablicę uchwytów zdarzeń `ppHandleArrayOut`, które mogą zawierać zdarzeń Kontynuuj uruchamiania dla środowiska CLR, w tym samym indeksie; oraz Rozmiar macierzy, `pdwArrayLengthOut`, która określa liczbę CLRs, które są ładowane.  
  
 W systemie operacyjnym Windows `debuggeePID` mapuje do systemu operacyjnego przetworzyć identyfikatora.  
  
 Pamięć `ppHandleArrayOut` i `ppStringArrayOut` są przydzielane przez tę funkcję. Aby zwolnić pamięć przydzielona, należy wywołać [CloseCLREnumeration, funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Ta funkcja może zostać wywołany z oba parametry tablicy ustawiona na wartość null, aby zwrócić liczbę CLRs w procesie docelowym. Z tej liczby obiekt wywołujący może wywnioskować rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
