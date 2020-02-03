---
title: Funkcja ProcessUnhandledException — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743924"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)
Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.  
  
 Używane przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>Parametry  
 errorMsg  
 Komunikat o błędzie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).  
  
 **BIBLIOTECE**  
  
 W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll  
  
 W .NET Framework 4 i nowszych: PresentationHost_v0400. dll  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
