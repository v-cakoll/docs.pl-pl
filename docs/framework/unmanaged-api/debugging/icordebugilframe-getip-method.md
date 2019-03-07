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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479769"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP — Metoda
Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, w tym artykule opisano, jak wartość wskaźnika instrukcji zostały pobrane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 [out] Wartość wskaźnika instrukcji.  
  
 `pMappingResult`  
 [out] Wskaźnik do bitowa kombinacja wartości wyliczenia cordebugmappingresult —, które opisują, jak wartość wskaźnika instrukcji zostały pobrane.  
  
## <a name="remarks"></a>Uwagi  
 Wartość wskaźnika instrukcji jest przesunięcie ramki stosu kod funkcji Microsoft intermediate language (MSIL). Jeśli ramka stosu jest aktywna, ten adres jest następną instrukcję do wykonania. Jeśli ramka stosu nie jest aktywny, ten adres jest następną instrukcję do wykonania podczas ponownego uaktywniania ramki stosu.  
  
 Jeśli ta ramka ramkę skompilowany just-in-time (JIT), wartość wskaźnika instrukcji będzie określana przez mapowanie wstecz od wskaźnika rzeczywiste natywnych instrukcji, co wartość może być tylko przybliżone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
