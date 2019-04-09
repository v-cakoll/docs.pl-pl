---
title: 'Środki zaradcze: Ścieżka dwukropek kontroli'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342c3ce59ad80c9a60f2a2b69b30f77ff0549415
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176764"
---
# <a name="mitigation-path-colon-checks"></a>Środki zaradcze: Ścieżka dwukropek kontroli
Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], wprowadzono szereg zmian obsługuje wcześniej nieobsługiwanych ścieżek, (zarówno pod względem długość i formatu). W szczególności sprawdza, czy składnia separator odpowiedniego dysku (dwukropek) wprowadzono bardziej poprawny.  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokować niektóre ścieżki identyfikatora URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody wcześniej obsługiwane.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aby obejść ten problem wcześniej akceptowalną ścieżką, która nie jest już obsługiwany przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, wykonasz następujące czynności:  
  
-   Ręcznie usuń schemat z adresu URL. Na przykład usunąć `file://` z adresu URL.  
  
-   Przekaż identyfikator URI do <xref:System.Uri> konstruktora i pobrać wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.  
  
-   Zrezygnować z nowych normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> przełączyć się do `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany przekierowania](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
