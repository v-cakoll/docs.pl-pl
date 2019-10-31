---
title: ICorDebugProcess::IsTransitionStub — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139389"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub — Metoda
Pobiera wartość wskazującą, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 podczas Wartość `CORDB_ADDRESS`, która określa dany adres.  
  
 `pbTransitionStub`  
 określoną Wskaźnik do wartości logicznej, która jest `true`, jeśli określony adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego; w przeciwnym wypadku *`pbTransitionStub` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `IsTransitionStub` może być używana przez niezarządzany kod wykonujący, aby określić, kiedy należy zwrócić kontrolę krokową do zarządzanego stepper.  
  
 Można również posłużyć do przechodzenia między zmianami, sprawdzając informacje w przenośnym pliku wykonywalnym (PE).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
