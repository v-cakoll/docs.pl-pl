---
title: Funkcja SaveToHistory — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731753"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)
Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.  
  
 Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pHistoryStream  
 Wskaźnik do strumienia historii.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll  
  
 W .NET Framework 4 i nowszych: PresentationHost_v0400. dll  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
