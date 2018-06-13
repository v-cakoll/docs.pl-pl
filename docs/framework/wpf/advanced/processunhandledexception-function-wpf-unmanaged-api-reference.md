---
title: Funkcja ProcessUnhandledException (WPF niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: bcde3fe6d3fdc1749f29a5c9f7625f802dd49535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544527"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>Funkcja ProcessUnhandledException (WPF niezarządzany wykaz interfejsów API)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używany przez infrastrukturę Windows Presentation Foundation (WPF) dla obsługi wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 errorMsg  
 Komunikat o błędzie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **BIBLIOTEKI DLL:**  
  
 W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll  
  
 **.NET framework w wersji:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Niezarządzane interfejsy API WPF — informacje](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
