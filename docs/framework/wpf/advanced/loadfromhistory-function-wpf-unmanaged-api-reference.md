---
title: "Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb68700ab0c11bbd6b09b83a826dc5ca4faa086
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)
Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
 Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 pHistoryStream  
 Wskaźnik do strumienia informacji historii.  
  
 pBindCtx  
 Wskaźnik do kontekstu powiązania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **BIBLIOTEKI DLL:**  
  
 W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll  
  
 W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll  
  
 **Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [WPF niezarządzany wykaz interfejsów API](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
