---
title: CreateCordbObject — Funkcja
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793857"
---
# <a name="createcordbobject-function"></a>CreateCordbObject — Funkcja
Tworzy interfejs debugera ([ICorDebug](icordebug-interface.md)), który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 podczas Wersja debugera procesu docelowego. Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.  
  
 `ppCordb`  
 określoną Wskaźnik na wskaźnik do obiektu, który będzie rzutowany do interfejsu [ICorDebug](icordebug-interface.md) i zwrócony.  
  
## <a name="return-value"></a>Wartość zwrócona  
 S_OK  
 Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 `ppCordb` ma wartość null lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci dla `ppCordb`  
  
 E_FAIL (lub inne kody powrotne E_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs [ICorDebug](icordebug-interface.md) , który jest zwracany w `ppCordb` jest interfejsem debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Library:** mscordbi_macx86.dll  
  
 **.NET Framework wersje:** 3,5 SP1
