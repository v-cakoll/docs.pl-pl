---
title: 'Środki zaradcze: sprawdzanie dwukropka ścieżki'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457898"
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

- [Zgodność aplikacji](application-compatibility.md)
