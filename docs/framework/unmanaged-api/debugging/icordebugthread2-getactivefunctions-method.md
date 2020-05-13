---
title: ICorDebugThread2::GetActiveFunctions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377154"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions — Metoda
Pobiera informacje o aktywnej funkcji w poszczególnych ramkach tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 podczas Rozmiar `pFunctions` tablicy.  
  
 `pcFunctions`  
 określoną Wskaźnik do liczby obiektów zwracanych w `pFunctions` tablicy. Liczba zwracanych obiektów będzie równa liczbie zarządzanych ramek na stosie.  
  
 `pFunctions`  
 [in. out] Tablica obiektów COR_ACTIVE_FUNCTION, z których każdy zawiera informacje o aktywnych funkcjach w ramkach tego wątku.  
  
 Pierwszy element zostanie użyty dla ramki liścia i tak dalej, jak z powrotem do korzenia stosu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `pFunctions` jest równa null, `GetActiveFunctions` zwraca tylko liczbę funkcji, które znajdują się na stosie. Oznacza to, że jeśli `pFunctions` wartość jest równa null przy wejściu, `GetActiveFunctions` Funkcja zwraca tylko wartości w `pcFunctions` .  
  
 `GetActiveFunctions`Metoda jest przeznaczona do optymalizacji nad uzyskaniem tych samych informacji z ramek w ślad stosu i zawiera tylko ramki, które miały obiekt ICorDebugILFrame dla nich w pełnym śladzie stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
