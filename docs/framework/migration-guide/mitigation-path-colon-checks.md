---
title: 'Środki zaradcze: Ścieżka dwukropek kontroli'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6799e36ec312bf857a12293dc0be15e9cc21f55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648454"
---
# <a name="mitigation-path-colon-checks"></a>Środki zaradcze: Ścieżka dwukropek kontroli
Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], wprowadzono szereg zmian obsługuje wcześniej nieobsługiwanych ścieżek, (zarówno pod względem długość i formatu). W szczególności sprawdza, czy składnia separator odpowiedniego dysku (dwukropek) wprowadzono bardziej poprawny.  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokować niektóre ścieżki identyfikatora URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody wcześniej obsługiwane.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aby obejść ten problem wcześniej akceptowalną ścieżką, która nie jest już obsługiwany przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metod, wykonasz następujące czynności:  
  
- Ręcznie usuń schemat z adresu URL. Na przykład usunąć `file://` z adresu URL.  
  
- Przekaż identyfikator URI do <xref:System.Uri> konstruktora i pobrać wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.  
  
- Zrezygnować z nowych normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> przełączyć się do `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
