---
title: CloseCLREnumeration — Funkcja
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961177"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration — Funkcja
Zamyka wszystkie prawidłowe typowe języka środowiska uruchomieniowego (języka wspólnego CLR) kontynuować uruchamianie zdarzenia znajdujące się w tablicy, uchwyt zwracany przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic ścieżka dojścia i parametry.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHandleArray`  
 [in] Wskaźnik do tablicy uchwytów zdarzeń zwróciło [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Wskaźnik do tablicy CLR ciąg ścieżki zwróciło [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] DWORD, zawierający rozmiaru (o długości) albo `pHandleArray` lub `pStringArray` (są one takie same).  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Uchwyty otwierane przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zostały zamknięte, i jest zwalniana pamięci przydzielonej dla tablic dojścia i parametry.  
  
 E_INVALIDARG  
 Długość `pHandleArray` pasuje do długości, który jest przekazywany `dwArrayLength`.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Funkcja nie może zwolnić pamięć dla `pHandleArray` i `pStringArray`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
