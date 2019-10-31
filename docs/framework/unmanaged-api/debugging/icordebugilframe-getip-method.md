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
ms.openlocfilehash: 7e1605eede55360e72d65da6744bc1dcce4f107f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130990"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP — Metoda
Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 określoną Wartość wskaźnika instrukcji.  
  
 `pMappingResult`  
 określoną Wskaźnik do bitowej kombinacji wartości wyliczenia CorDebugMappingResult —, który opisuje sposób uzyskiwania wartości wskaźnika instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Wartość wskaźnika instrukcji to przesunięcie ramki stosu do kodu języka pośredniego firmy Microsoft (MSIL) funkcji. Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcją do wykonania. Jeśli ramka stosu nie jest aktywna, ten adres jest następną instrukcją do wykonania po ponownym uaktywnieniu ramki stosu.  
  
 Jeśli ta ramka jest skompilowaną ramką just-in-Time (JIT), wartość wskaźnika instrukcji zostanie określona przez mapowanie wstecz od rzeczywistego wskaźnika instrukcji natywnych, więc wartość może być przybliżona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
