---
title: LoadFromHistory, funkcja (niezarządzany wykaz interfejsów API WPF.)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 42be46d836a299139bded938237fe2a06e9794a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646936"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory, funkcja (niezarządzany wykaz interfejsów API WPF.)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemem windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 pHistoryStream  
 Wskaźnik do strumienia danych historii.  
  
 pBindCtx  
 Wskaźnik do kontekstu powiązania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL:**  
  
 W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W programie .NET Framework 4 i nowszych wersji: PresentationHost_v0400.dll  
  
 **Wersja programu .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Niezarządzane interfejsy API WPF — informacje](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
