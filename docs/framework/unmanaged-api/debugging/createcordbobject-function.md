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
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179233"
---
# <a name="createcordbobject-function"></a>CreateCordbObject — Funkcja
Tworzy interfejs debugera[(ICorDebug),](icordebug-interface.md)który zapewnia funkcje tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [w] Debuger wersji procesu docelowego. Ten parametr musi być CorDebugVersion_2_0 do zdalnego debugowania.  
  
 `ppCordb`  
 [na zewnątrz] Wskaźnik do wskaźnika do obiektu, który zostanie rzutowania do interfejsu [ICorDebug](icordebug-interface.md) i zwrócone.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Liczba clr w procesie została pomyślnie określona, a odpowiednie tablice dojścia i ścieżki zostały poprawnie wypełnione.  
  
 E_invalidarg  
 `ppCordb`jest null `iDebuggerVersion` lub nie jest CorDebugVersion_2_0.  
  
 E_outofmemory  
 Nie można przydzielić wystarczającej ilości pamięci`ppCordb`  
  
 E_FAIL (lub inne E_ kody zwrotne)  
 Inne awarie.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs [ICorDebug,](icordebug-interface.md) który `ppCordb` jest zwracany w jest interfejs debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje .NET Framework:** 3.5 SP1
