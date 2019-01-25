---
title: ICorDebugMergedAssemblyRecord::GetCulture Method
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fd66ee28ca276aaa31e1e92a42d0fd88ff00d89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654967"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture Method
Pobiera ciąg nazwy kultury zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchCulture`  
 [in] Liczba znaków w `szCulture` buforu.  
  
 `pcchCulture`  
 [out] Liczba znaków rzeczywiście zapisanych na `szCulture` buforu.  
  
 `szCulture`  
 [out] Tablica znaków, który zawiera nazwę kultury.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa kultury jest unikatowy ciąg, który identyfikuje kultury, na przykład "en US" (w przypadku kultury angielski (Stany Zjednoczone)) lub "neutralnej" (dla kultury neutralnej).  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
