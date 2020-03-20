---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178529"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>Metoda ICorDebugProcess6::GetExportStepInfo
Zawiera informacje na temat wyeksportowanych funkcji środowiska wykonawczego, aby ułatwić przechodzenie przez kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametry  
 pszExportName  
 [w] Nazwa funkcji eksportu środowiska uruchomieniowego, jak zapisano w tabeli eksportu pe.  
  
 invokeKind  
 [na zewnątrz] Wskaźnik do członka wyliczenia [CorDebugCodeInvokeKind,](cordebugcodeinvokekind-enumeration.md) który opisuje, jak wyeksportowana funkcja wywoła kod zarządzany.  
  
 invokePurpose  
 [na zewnątrz] Wskaźnik do członka wyliczenia [CorDebugCodeInvokePurpose,](cordebugcodeinvokepurpose-enumeration.md) który opisuje, dlaczego wyeksportowana funkcja wywoła kod zarządzany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda może zwracać wartości wymienione w poniższej tabeli.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`S_OK`|Wywołanie metody zakończyło się pomyślnie.|  
|`E_POINTER`|`pInvokeKind`lub `pInvokePurpose` ma **wartość null**.|  
|Inne `HRESULT` wartości, które nie po awarii.|W stosownych przypadkach.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
