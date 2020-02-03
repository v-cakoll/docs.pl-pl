---
title: Funkcja ForwardTranslateAccelerator — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747035"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)
Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.  
  
 Używany przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pMsg  
 Wskaźnik do komunikatu.  
  
 appUnhandled  
 `true`, gdy aplikacja uzyskała już szansę obsługi wiadomości wejściowej, ale jej nie została obsłużona; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).  
  
 **BIBLIOTECE**  
  
 W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll  
  
 W .NET Framework 4 i nowszych: PresentationHost_v0400. dll  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
