---
title: ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 73480f7cd8be7bcb5296782a8503eb689442a14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578643"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException, funkcja (niezarządzany wykaz interfejsów API WPF.)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używana przez infrastrukturę Windows Presentation Foundation (WPF) do obsługi wyjątku.  
  
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
 **Platformy:** Zobacz [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll  
  
 **Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Niezarządzane interfejsy API WPF — informacje](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
