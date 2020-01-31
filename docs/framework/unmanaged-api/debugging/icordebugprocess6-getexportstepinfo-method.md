---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 118f52db63464b4c9355ba9ee7f330b996c5bf71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792247"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>Metoda ICorDebugProcess6::GetExportStepInfo
Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametry  
 pszExportName  
 podczas Nazwa funkcji eksportu środowiska uruchomieniowego, która została zapisywana w tabeli eksportu PE.  
  
 invokeKind  
 określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) , który opisuje sposób, w jaki wyeksportowana funkcja wywoła kod zarządzany.  
  
 invokePurpose  
 określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) , który opisuje, dlaczego wyeksportowana funkcja wywoła kod zarządzany.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda może zwracać wartości wymienione w poniższej tabeli.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`S_OK`|Wywołanie metody zakończyło się pomyślnie.|  
|`E_POINTER`|`pInvokeKind` lub `pInvokePurpose` ma **wartość null**.|  
|Inne błędne wartości `HRESULT`.|Zgodnie z potrzebami.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
