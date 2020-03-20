---
title: ICorDebugILFrame::GetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178822"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP — Metoda
Pobiera wartość wskaźnika instrukcji i bitowej wartości kombinacji, która opisuje, jak uzyskano wartość wskaźnika instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 [na zewnątrz] Wartość wskaźnika instrukcji.  
  
 `pMappingResult`  
 [na zewnątrz] Wskaźnik do bitowej kombinacji corDebugMappingResult wartości wyliczenia, które opisują, jak wartość wskaźnika instrukcji został uzyskany.  
  
## <a name="remarks"></a>Uwagi  
 Wartość wskaźnika instrukcji jest przesunięcie ramki stosu do funkcji Microsoft pośredniego języka (MSIL) kod. Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcją do wykonania. Jeśli ramka stosu nie jest aktywna, ten adres jest następną instrukcją do wykonania po ponownym uaktywnieniu ramki stosu.  
  
 Jeśli ta ramka jest klatką skompilowaną just-in-time (JIT), wartość wskaźnika instrukcji zostanie określona przez mapowanie wstecz z rzeczywistego wskaźnika instrukcji natywnej, więc wartość może być tylko przybliżona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
