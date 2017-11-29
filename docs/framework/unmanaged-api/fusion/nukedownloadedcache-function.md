---
title: "NukeDownloadedCache — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff24cf46ab24fe94ab19cee04d9e32ed1a34b53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache — Funkcja
Usuwa wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) pamięć podręczną pobierania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h.  
  
## <a name="remarks"></a>Uwagi  
 Pamięć podręczną pobierania CLR jest obszar przechowywania zestawy o silnych nazwach, które są pobierane z adresu URL do możliwości ponownego użycia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** Fusion.dll i Mscorwks.dll.a;a;pierwsza. Użyj Fusion.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Createhistoryreader — funkcja](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [Gethistoryfiledirectory — funkcja](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
