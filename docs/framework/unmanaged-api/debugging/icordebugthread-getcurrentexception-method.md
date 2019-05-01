---
title: ICorDebugThread::GetCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994035"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException — Metoda
Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który przedstawia wyjątek, który obecnie został zgłoszony przez kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 [out] Wskaźnik na adres `ICorDebugValue` obiekt, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wyjątku będzie istnieć od momentu wyjątek aż do końca `catch` bloku. Obliczanie funkcji, które jest wykonywane za pomocą metod ICorDebugEval, należy usunąć obiekt wyjątku na temat instalacji, a następnie przywróć ją po zakończeniu.  
  
 Wyjątki mogą być zagnieżdżane (na przykład, jeśli wyjątek jest zgłaszany w filtrze lub obliczanie funkcji), dlatego może być wiele wyjątków oczekujących w jednym wątku. `GetCurrentException` Zwraca najbardziej bieżącego wyjątku.  
  
 Obiekt wyjątku i typu mogą ulec zmianie w całym cyklu życia wyjątku. Na przykład po typu x jest zwracany wyjątek, środowisko uruchomieniowe języka wspólnego (CLR) może przekroczyć dostępną ilość pamięci i podwyższyć jego poziom do wyjątku braku pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
