---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d6ac2967b4314a57aa30bbb34ff3d354a6365
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint — Metoda
Ustawia niezarządzanego punktu przerwania w przesunięciu określonego obrazu macierzystego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` obiekt, który określa przesunięcie obrazu macierzystego.  
  
 `bufsize`  
 [in] Rozmiar w bajtach z `buffer` tablicy.  
  
 `buffer`  
 [out] Tablica zawiera kod operacji, która zastępuje punktu przerwania.  
  
 `bufLen`  
 [out] Wskaźnik do liczba bajtów zwrócona w `buffer` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku przesunięcie obrazu macierzystego w środowisko uruchomieniowe języka wspólnego (CLR), punkt przerwania zostanie zignorowany. Dzięki temu CLR w celu uniknięcia wysyłki przerwania poza pasmem, gdy punkt przerwania jest ustawiony przez debuger.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
