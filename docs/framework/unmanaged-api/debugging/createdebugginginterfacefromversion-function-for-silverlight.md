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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968956b513e1ae80a25f5fb4afea48bf888876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739266"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight
Akceptuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) wersja ciąg, który jest zwracany z [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedniego interfejsu debugera (zazwyczaj [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDebuggeeVersion`  
 [in] Ciąg wersji środowiska CLR w debugowanym obiekcie docelowym, która jest zwracana przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Wskaźnik do wskaźnika do obiektu COM (`IUnknown`). Ten obiekt zostanie rzutowany [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt przed zwróceniem.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 `ppCordb` odwołuje się do prawidłowego obiektu, który implementuje [icordebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu.  
  
 E_INVALIDARG  
 Albo `szDebuggeeVersion` lub `ppCordb` ma wartość null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Składnik, który jest konieczny, aby debugowanie CLR nie można odnaleźć. Oznacza to, że plik mscordbi.dll lub mscordaccore.dll nie został znaleziony w tym samym katalogu jako element docelowy CoreCLR.dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Plik mscordbi.dll lub mscordaccore.dll nie jest tę samą wersję, jako cel CoreCLR.dll.  
  
 E_FAIL (lub inne kody powrotne e_)  
 Nie można zwrócić [icordebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Uwagi  
 Interfejs, który jest zwracany udostępnia funkcje służące do dołączania do CLR w procesie docelowym i debugowania kodu zarządzanego, który działa środowisko CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** dbgshim.h  
  
 **Biblioteka:** dbgshim.dll  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1
