---
title: Funkcja CreateIDispatchSTAForwarder — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174722"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>Funkcja CreateIDispatchSTAForwarder (odwołanie do interfejsu API niezarządzanego WPF)
Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.  
  
 Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania wątkami i oknami.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 pDispatchDelegate  
 Wskaźnik do `IDispatch` interfejsu.  
  
 ppForwarder (Polski)  
 Wskaźnik do adresu `IDispatch` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll  
  
 **Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
