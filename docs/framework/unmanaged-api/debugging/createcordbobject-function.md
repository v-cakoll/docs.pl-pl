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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ab86277956469e558d20cea81174a7fdcc0020b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739326"
---
# <a name="createcordbobject-function"></a>CreateCordbObject — Funkcja
Tworzy interfejs debugera ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) zapewnia funkcje tworzenia wystąpienia zarządzanego sesji debugowania zdalnego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Wersja debugera procesu docelowego. Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.  
  
 `ppCordb`  
 [out] Wskaźnik do wskaźnika do obiektu, który będzie można rzutować [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs i zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 `ppCordb` ma wartość null, lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do `ppCordb`  
  
 E_FAIL (lub inne kody powrotne e_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs, który jest zwracany w `ppCordb` jest najwyższego poziomu interfejsu debugowania dla wszystkich zarządzanych usług debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Library:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
