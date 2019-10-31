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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139930"
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
 podczas Rozmiar tablicy `pFunctions`.  
  
 `pcFunctions`  
 określoną Wskaźnik do liczby obiektów zwracanych w tablicy `pFunctions`. Liczba zwracanych obiektów będzie równa liczbie zarządzanych ramek na stosie.  
  
 `pFunctions`  
 [in. out] Tablica obiektów COR_ACTIVE_FUNCTION, z których każdy zawiera informacje o aktywnych funkcjach w ramkach tego wątku.  
  
 Pierwszy element zostanie użyty dla ramki liścia i tak dalej, jak z powrotem do korzenia stosu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pFunctions` ma wartość null przy wejściu, `GetActiveFunctions` zwraca tylko liczbę funkcji, które znajdują się na stosie. Oznacza to, że jeśli `pFunctions` ma wartość null przy wejściu, `GetActiveFunctions` zwraca wartość tylko w `pcFunctions`.  
  
 Metoda `GetActiveFunctions` jest przeznaczona do optymalizacji nad uzyskaniem tych samych informacji z ramek w śladach stosu i zawiera tylko ramki, które miały obiekt ICorDebugILFrame dla nich w pełnym śladzie stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
