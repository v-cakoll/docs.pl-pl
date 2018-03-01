---
title: "ICorDebugThread2::GetActiveFunctions — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions — Metoda
Pobiera informacje o funkcji active w każdej z ramek tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] Rozmiar `pFunctions` tablicy.  
  
 `pcFunctions`  
 [out] Wskaźnik do liczba obiektów zwrócona w `pFunctions` tablicy. Liczba zwróconych obiektów będzie równa liczbie zarządzanych ramek na stosie.  
  
 `pFunctions`  
 [w, out] Tablica obiektów cor_active_function —, z których każdy zawiera informacje na temat funkcji active w ramkach tego wątku.  
  
 Pierwszy element będzie służyć do ramki typu liść i itd. wstecz do katalogu głównego stosu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca liczbę funkcji, które znajdują się na stosie. Oznacza to, że jeśli `pFunctions` ma wartość null w danych wejściowych, `GetActiveFunctions` zwraca wartość tylko w `pcFunctions`.  
  
 `GetActiveFunctions` — Metoda jest przeznaczona do optymalizacji na pobieranie tych samych informacji z klatek ślad stosu i zawiera tylko ramki, które było obiektu ICorDebugILFrame ich w ślad stosu pełna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
