---
title: Funkcja SetFakeActiveWindow (WPF niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SetFakeActiveWindow
api_location:
- PresentationHost_v0400.dll
ms.assetid: a69118be-63b0-445c-9fb6-ab8cc958e531
ms.openlocfilehash: 6eb8d4d4b04e80373b8bfe1ceed84694e2a8a469
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544589"
---
# <a name="setfakeactivewindow-function-wpf-unmanaged-api-reference"></a>Funkcja SetFakeActiveWindow (WPF niezarządzany wykaz interfejsów API)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall SetFakeActiveWindow(  
   HWND hwnd  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 Właściwość hwnd  
 Uchwyt okna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Biblioteki DLL:** PresentationHost_v0400.dll  
  
 **.NET framework w wersji:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Niezarządzane interfejsy API WPF — informacje](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
