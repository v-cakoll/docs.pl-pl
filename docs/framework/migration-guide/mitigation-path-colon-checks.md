---
title: Środki zaradcze Sprawdzanie dwukropek ścieżki
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789989"
---
# <a name="mitigation-path-colon-checks"></a>Środki zaradcze Sprawdzanie dwukropek ścieżki
Począwszy od aplikacji odnoszących się do .NET Framework 4.6.2, wprowadzono wiele zmian do obsługi poprzednio nieobsługiwanych ścieżek (zarówno pod względem długości, jak i formatu). W szczególności sprawdza poprawność składni separatora dysku (dwukropek).  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokują niektóre ścieżki URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, które wcześniej były obsługiwane.  
  
## <a name="mitigation"></a>Ograniczenie  
 Aby obejść problem z wcześniej akceptowalną ścieżką, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> metody <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> i, można wykonać następujące czynności:  
  
- Ręcznie usuń schemat z adresu URL. Na przykład Usuń `file://` adres URL.  
  
- Przekaż identyfikator URI do <xref:System.Uri> konstruktora i Pobierz wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.  
  
- Zrezygnuj z nowej normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> przełącznik na `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-2.md)
