---
title: "EnumerateCLRs — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EnumerateCLRs
api_location: dbgshim.dll
api_type: COM
f1_keywords: EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6539b471d6a3075bb4cec69b382cf7702a439d5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs — Funkcja
Udostępnia mechanizm dla wyliczania CLRs w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [in] Proces identyfikator procesu, z którego będzie można wyliczyć CLRs załadowany.  
  
 `ppHandleArrayOut`  
 [out] Wskaźnik do tablicę zawierającą uchwyty zdarzenie, które są używane do kontynuować uruchamianie środowiska CLR. Każdy dojście do tablicy nie jest gwarantowana jest nieprawidłowy. Jeśli prawidłowe, dojście ma być używany jako zdarzenie uruchomienia Kontynuuj odpowiedniego środowiska uruchomieniowego znajduje się w tym samym indeksie `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Wskaźnik do tablicy ciągów, które określają pełnej ścieżki do CLRs załadowany w procesie.  
  
 `pdwArrayLengthOut`  
 [out] Wskaźnik do typu DWORD, który zawiera długości równej wielkości `ppHandleArrayOut` i `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 Albo `ppHandleArrayOut` lub `ppStringArrayOut` ma wartość null, lub `pdwArrayLengthOut` ma wartość null.  
  
 E_OUTOFMEMORY  
 Funkcji nie może przydzielić wystarczającej ilości pamięci dla tablic dojścia i ścieżka.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można wyliczyć CLRs załadowany.  
  
## <a name="remarks"></a>Uwagi  
 Dla procesu docelowego, który jest identyfikowany przez `debuggeePID`, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`, do CLRs załadowany w procesie; tablicę uchwytów zdarzeń `ppHandleArrayOut`, które mogą zawierać zdarzeń Kontynuuj uruchamiania dla CLR w tym samym indeksie; i rozmiar tablic, `pdwArrayLengthOut`, która określa liczbę CLRs, które zostały załadowane.  
  
 W systemie operacyjnym Windows `debuggeePID` identyfikator przetworzyć map do systemu operacyjnego.  
  
 Pamięć `ppHandleArrayOut` i `ppStringArrayOut` są przydzielane przez tę funkcję. Aby zwolnić pamięć przydzielona, należy wywołać [closeclrenumeration — funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Ta funkcja może zostać wywołana z obu parametrów tablicowych ustawiona na wartość null, aby uzyskać liczbę CLRs w procesie docelowym. Z licznik ten obiekt wywołujący może wnioskować rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** biblioteki dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
