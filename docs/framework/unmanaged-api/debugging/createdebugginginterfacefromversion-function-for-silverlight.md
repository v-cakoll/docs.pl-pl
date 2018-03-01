---
title: "CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight
Akceptuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) ciąg wersji zwrócone przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedniego interfejsu debugera (zazwyczaj [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDebuggeeVersion`  
 [in] Ciąg wersji aparatu CLR w debugowanym obiekcie docelowym, który jest zwracany przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Wskaźnik na wskaźnik do obiektu modelu COM (`IUnknown`). Ten obiekt będzie rzutowany [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt przed zwróceniem jest.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 `ppCordb`odwołuje się do prawidłowego obiektu, który implementuje [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu.  
  
 E_INVALIDARG  
 Albo `szDebuggeeVersion` lub `ppCordb` ma wartość null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Nie można zlokalizować składnika, który jest konieczny, aby debugowanie CLR. Oznacza to, że plik mscordbi.dll lub mscordaccore.dll nie znaleziono w tym samym katalogu co element docelowy CoreCLR.dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Plik mscordbi.dll lub mscordaccore.dll nie jest ta sama wersja jako cel CoreCLR.dll.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można zwrócić [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Uwagi  
 Interfejs, który jest zwracany zapewnia funkcji dołączanie do środowiska CLR w procesie docelowym i debugowanie kodu zarządzanego, uruchomionym środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** biblioteki dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
