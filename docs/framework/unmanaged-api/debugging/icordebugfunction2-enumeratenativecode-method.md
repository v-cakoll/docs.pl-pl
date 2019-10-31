---
title: ICorDebugFunction2::EnumerateNativeCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: d5b24ee02a682b38dcf0cb3449f0dff197e91bf9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137829"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode — Metoda
Pobiera wskaźnik interfejsu do obiektu ICorDebugCodeEnum, który zawiera instrukcje kodu natywnego w funkcji, do której odwołuje się ten obiekt ICorDebugFunction2.  
  
> [!NOTE]
> `EnumerateNativeCode` nie jest zaimplementowana w bieżącej wersji .NET Framework.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorDebug. idl, CorDebug. h
