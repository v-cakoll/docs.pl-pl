---
title: "ICorDebugArrayValue::GetBaseIndicies — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 820d81b4538c3cf2bf6fa123df2012ea06e2d978
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a>ICorDebugArrayValue::GetBaseIndicies — Metoda
Pobiera podstawowy indeks każdego wymiaru tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdim`  
 [in] Liczba wymiarów tego `ICorDebugArrayValue` obiektu. Ta wartość jest również rozmiar `indicies` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.  
  
 `indicies`  
 [out] Tablica liczb całkowitych, z których każdy jest indeksem podstawowej (to znaczy indeks początkowy) wymiaru tego `ICorDebugArrayValue` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
