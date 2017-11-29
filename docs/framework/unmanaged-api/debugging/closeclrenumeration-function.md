---
title: "CloseCLREnumeration — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
