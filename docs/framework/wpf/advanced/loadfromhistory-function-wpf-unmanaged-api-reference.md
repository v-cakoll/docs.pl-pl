---
title: Funkcja LoadFromHistory — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727928"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)
Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.  
  
 Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pHistoryStream  
 Wskaźnik do strumienia informacji o historii.  
  
 pBindCtx  
 Wskaźnik do kontekstu powiązania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll  
  
 W .NET Framework 4 i nowszych: PresentationHost_v0400. dll  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
