---
title: 'Ograniczenie: Ścieżka dwukropek kontroli'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a54220a90a5120d13c89232d30ab40140c324097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387383"
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
