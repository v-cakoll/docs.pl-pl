---
title: ForwardTranslateAccelerator, funkcja — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186629"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator, funkcja (odwołanie do interfejsu API niezarządzanego WPF)
Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.  
  
 Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania systemem Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pMsg  
 Wskaźnik do wiadomości.  
  
 appNieręczny  
 `true`gdy aplikacja ma już szansę obsłużyć komunikat wejściowy, ale nie obsługuje go; w `false`przeciwnym razie , .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll  
  
 **Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
