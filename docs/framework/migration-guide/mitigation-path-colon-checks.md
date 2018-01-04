---
title: "Ograniczenie: Ścieżka dwukropek kontroli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a976e4491924f91e97f01a9b98db945699655196
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-path-colon-checks"></a>Ograniczenie: Ścieżka dwukropek kontroli
Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], liczba zmiany zostały wprowadzone obsługuje wcześniej nieobsługiwany ścieżek, (zarówno długość i format). W szczególności sprawdzanie składni separatora właściwego dysku (dwukropek) wprowadzono więcej poprawne.  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokować niektóre ścieżki identyfikatora URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody wcześniej obsługiwane.  
  
## <a name="mitigation"></a>Ograniczenie  
 W celu obejścia problemu wcześniej dopuszczalne ścieżki, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, można wykonaj następujące czynności:  
  
-   Ręcznie usuń system z adresu URL. Na przykład usunąć `file://` z adresu URL.  
  
-   Identyfikator URI do przekazania <xref:System.Uri> konstruktora i pobrać wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.  
  
-   Zrezygnować z nowego normalizacji ścieżka przez ustawienie `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> przełączyć się do `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
