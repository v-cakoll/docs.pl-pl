---
title: ICorDebugMergedAssemblyRecord::Metoda GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178754"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetCulture
Pobiera ciąg nazwy kultury zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchCulture`  
 [w] Liczba znaków w `szCulture` buforze.  
  
 `pcchCulture`  
 [na zewnątrz] Liczba znaków faktycznie zapisanych `szCulture` w buforze.  
  
 `szCulture`  
 [na zewnątrz] Tablica znaków zawierająca nazwę kultury.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa kultury jest unikatowy ciąg, który identyfikuje kultury, takich jak "en-US" (dla kultury angielski (Stany Zjednoczone) lub "neutralny" (dla kultury neutralnej).  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
