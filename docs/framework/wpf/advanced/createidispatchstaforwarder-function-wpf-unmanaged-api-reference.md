---
title: Funkcja CreateIDispatchSTAForwarder — dokumentacja interfejsu API Unmanaged WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738032"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder — funkcja (odwołanie do niezarządzanego interfejsu API platformy WPF)
Ten interfejs API obsługuje infrastrukturę Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio w kodzie.  
  
 Używany przez infrastrukturę Windows Presentation Foundation (WPF) dla wątków i zarządzania systemem Windows.  
  
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
 Wskaźnik do interfejsu `IDispatch`.  
  
 ppForwarder  
 Wskaźnik do adresu interfejsu `IDispatch`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 W .NET Framework 3,0 i 3,5: PresentationHostDLL. dll  
  
 W .NET Framework 4 i nowszych: PresentationHost_v0400. dll  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
