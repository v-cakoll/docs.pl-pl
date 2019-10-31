---
title: 'Środki zaradcze: sprawdzanie dwukropka ścieżki'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: ee71f6ef1e70509e772aee2cc75d00c33122a92e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126229"
---
# <a name="mitigation-path-colon-checks"></a>Środki zaradcze: sprawdzanie dwukropka ścieżki
Począwszy od aplikacji odnoszących się do .NET Framework 4.6.2, wprowadzono wiele zmian do obsługi poprzednio nieobsługiwanych ścieżek (zarówno pod względem długości, jak i formatu). W szczególności sprawdza poprawność składni separatora dysku (dwukropek).  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokują niektóre ścieżki URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, które wcześniej były obsługiwane.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aby obejść problem z wcześniej akceptowalną ścieżką, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, można wykonać następujące czynności:  
  
- Ręcznie usuń schemat z adresu URL. Na przykład Usuń `file://` z adresu URL.  
  
- Przekaż identyfikator URI do konstruktora <xref:System.Uri> i Pobierz wartość właściwości <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.  
  
- Zrezygnuj z nowej normalizacji ścieżki, ustawiając przełącznik `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> do `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-2.md)
