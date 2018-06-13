---
title: Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: d8a296c0590d07c4929610021714d2a257236d67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542564"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 pMsg  
 Wskaźnik do wiadomości.  
  
 appUnhandled  
 `true` gdy aplikacja została już podana możliwość obsługi komunikatu wejściowego, ale nie jest obsługiwane. w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **BIBLIOTEKI DLL:**  
  
 W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll  
  
 **.NET framework w wersji:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Niezarządzane interfejsy API WPF — informacje](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
