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
ms.openlocfilehash: 18903bd00b0a9d09365d03c155531a25dc013189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406091"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration — Funkcja
Zamyka żadnych prawidłowy wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kontynuować uruchamianie zdarzenia znajdujące się w tablicy dojść zwrócony przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic dojście i ciągu ścieżki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHandleArray`  
 [in] Wskaźnik do tablicy uchwytów zdarzeń zwrócony z [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Wskaźnik do tablicy CLR ciąg ścieżki zwrócony z [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] DWORD zawierający rozmiaru (długość) albo `pHandleArray` lub `pStringArray` (są one takie same).  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Uchwyty otwarty przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) są zamknięte i zostanie zwolniona pamięć przydzielona dla tablic dojście i ciąg.  
  
 E_INVALIDARG  
 Długość `pHandleArray` nie odpowiada długości, który jest przekazywany w `dwArrayLength`.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można zwolnić pamięć jest funkcja `pHandleArray` i `pStringArray`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** biblioteki dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
