---
title: WAITORTIMERCALLBACK — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: ee5dd611888ec52e360ef45fab4c01e9c5b2d6bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009455"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK — Wskaźnik funkcji
Wskazuje funkcję, która powiadamia hosta o <xref:System.Threading.WaitHandle> zasygnalizowaniu lub przekroczeniu limitu czasu dojścia oczekiwania ().  
  
 Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpParameter`  
 podczas Wskaźnik do obiektu, który zawiera informacje zdefiniowane przez hosta.  
  
 `TimerOrWaitFired`  
 [w] `true` Jeśli upłynął limit czasu dojścia oczekiwania lub `false` Jeśli został on zasygnalizowani.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja, do której `WAITORTIMERCALLBACK` punkty jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorWks. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
