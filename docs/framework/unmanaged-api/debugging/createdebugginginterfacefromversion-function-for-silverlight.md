---
title: CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 85b5a5a630f399d0e036de434365e2e4f8f02dea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793829"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight
Akceptuje ciąg wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest zwracany przez [funkcję CreateVersionStringFromModule —](createversionstringfrommodule-function.md)i zwraca odpowiedni interfejs debugera (zazwyczaj [ICorDebug](icordebug-interface.md)).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDebuggeeVersion`  
 podczas Ciąg wersji środowiska CLR w docelowym debugowanego obiektu, który jest zwracany przez [funkcję CreateVersionStringFromModule —](createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 określoną Wskaźnik na wskaźnik do obiektu COM (`IUnknown`). Ten obiekt będzie rzutowany na obiekt [ICorDebug](icordebug-interface.md) przed jego zwróceniem.  
  
## <a name="return-value"></a>Wartość zwrócona  
 S_OK  
 `ppCordb` odwołuje się do prawidłowego obiektu, który implementuje interfejs [interfejsu ICorDebug](icordebug-interface.md) .  
  
 E_INVALIDARG  
 `szDebuggeeVersion` lub `ppCordb` ma wartość null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Nie można zlokalizować składnika, który jest niezbędny do debugowania CLR. Oznacza to, że plik mscordbi. dll lub mscordaccore. dll nie został odnaleziony w tym samym katalogu co element docelowy CoreCLR. dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Mscordbi. dll lub mscordaccore. dll nie jest taka sama jak wersja elementu docelowego CoreCLR. dll.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Nie można zwrócić [interfejsu ICorDebug](icordebug-interface.md).  
  
## <a name="remarks"></a>Uwagi  
 Interfejs, który jest zwracany, udostępnia funkcje do dołączania do środowiska CLR w procesie docelowym i debugowania kodu zarządzanego, który działa środowisko CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim. h  
  
 **Biblioteka:** dbgshim. dll  
  
 **.NET Framework wersje:** 3,5 SP1
