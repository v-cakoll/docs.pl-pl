---
title: Funkcja LoadFromHistory — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141578"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Funkcja LoadFromHistory (odwołanie do niezarządzanego interfejsu API WPF WPF)
Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.  
  
 Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania systemem Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>Parametry  
 pHistoryStream (Strumień historii)  
 Wskaźnik do strumienia informacji o historii.  
  
 pBindCtx (właśc.  
 Wskaźnik do kontekstu powiązania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Dll:**  
  
 W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll  
  
 **Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Niezarządzane interfejsy API WPF — informacje](wpf-unmanaged-api-reference.md)
