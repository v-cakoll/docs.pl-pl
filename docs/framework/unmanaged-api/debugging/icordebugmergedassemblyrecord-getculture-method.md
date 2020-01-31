---
title: 'ICorDebugMergedAssemblyRecord:: getculture — Metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: 77ad8ee7977096e87b9fd2e131920a042243560e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793155"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord:: getculture — Metoda
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
 podczas Liczba znaków w buforze `szCulture`.  
  
 `pcchCulture`  
 określoną Liczba znaków rzeczywiście zapisywana w buforze `szCulture`.  
  
 `szCulture`  
 określoną Tablica znaków, która zawiera nazwę kultury.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa kultury jest unikatowym ciągiem, który identyfikuje kulturę, na przykład "en-US" (dla kultury angielskiej (Stany Zjednoczone)) lub "neutralną" (dla kultury neutralnej).  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
