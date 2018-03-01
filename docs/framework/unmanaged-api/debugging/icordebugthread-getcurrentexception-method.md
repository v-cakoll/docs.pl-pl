---
title: "ICorDebugThread::GetCurrentException — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException — Metoda
Pobiera wskaźnika interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 [out] Wskaźnik do adresu `ICorDebugValue` obiekt, który reprezentuje wyjątek, który obecnie został zgłoszony przez kod zarządzany.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wyjątku będzie istnieć od czasu wyjątku do końca `catch` bloku. Obliczanie funkcji, które jest wykonywane za pomocą metod ICorDebugEval, należy usunąć obiekt wyjątku w instalacji, a następnie przywróć ją po zakończeniu.  
  
 Wyjątki mogą być zagnieżdżane (na przykład, jeśli w filtrze lub obliczanie funkcji jest zgłaszany wyjątek), dlatego może być wiele oczekujących wyjątków w jednym wątku. `GetCurrentException`Zwraca najbardziej bieżącego wyjątku.  
  
 Obiekt wyjątku i typ mogą ulec zmianie przez cały czas życia wyjątku. Na przykład po wyjątek typu x, środowisko uruchomieniowe języka wspólnego (CLR) może przekroczyć dostępną ilość pamięci i Podwyższ go do wyjątku braku pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
