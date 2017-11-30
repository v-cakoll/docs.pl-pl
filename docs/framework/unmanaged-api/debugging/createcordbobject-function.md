---
title: "CreateCordbObject — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCoredbObject
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06e08148e5526d65d82eca52ffe8db66a4e7df6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createcordbobject-function"></a>CreateCordbObject — Funkcja
Tworzy interfejs debugera ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) zapewnia funkcje w uruchamianiu sesji debugowania zarządzanego dla procesu zdalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Wersja debugera procesu docelowego. Ten parametr musi być CorDebugVersion_2_0 do zdalnego debugowania.  
  
 `ppCordb`  
 [out] Wskaźnik na wskaźnik do obiektu, który będzie można rzutować na [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu i zwracany.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 CLRs procesu został pomyślnie określana i odpowiednie dojścia tablice ścieżki zostały prawidłowo wypełnione.  
  
 E_INVALIDARG  
 `ppCordb`ma wartość null, lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.  
  
 E_OUTOFMEMORY  
 Nie można przydzielić wystarczającej ilości pamięci do`ppCordb`  
  
 E_FAIL (lub inne kody powrotu E_)  
 Inne błędy.  
  
## <a name="remarks"></a>Uwagi  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs, który jest zwracany w `ppCordb` jest najwyższego poziomu interfejsu debugowania dla wszystkich zarządzanych usług debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Biblioteka:** mscordbi_macx86.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
