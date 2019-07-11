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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf3998d7430348cb71af8e7dd75cf2203d380ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769033"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions — Metoda
Pobiera informacje o funkcji aktywnych we wszystkich ramki dla wątku.  
  
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
 [in] Rozmiar `pFunctions` tablicy.  
  
 `pcFunctions`  
 [out] Wskaźnik do liczby obiektów zwróconych w `pFunctions` tablicy. Liczba obiektów zwróconych będzie równa liczbie zarządzanych ramek na stosie.  
  
 `pFunctions`  
 [out w] Tablica obiektów cor_active_function —, z których każdy zawiera informacje na temat funkcji active w ramkach tego wątku.  
  
 Pierwszy element stosowanych w odniesieniu do ramki liścia i itd wstecz do katalogu głównego stosu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca liczbę funkcji, które znajdują się w stosie. Oznacza to jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca wartość tylko w `pcFunctions`.  
  
 `GetActiveFunctions` Metoda jest przeznaczona do optymalizacji na pobieranie tych samych informacji z ramek w ślad stosu i zawiera tylko ramki, które będą miały obiektu ICorDebugILFrame ich w pełen ślad stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
