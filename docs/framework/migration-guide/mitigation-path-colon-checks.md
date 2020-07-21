---
title: 'Środki zaradcze: sprawdzanie dwukropka ścieżki'
description: Dowiedz się więcej o zmianach wprowadzonych w .NET Framework 4.6.2 do obsługi sprawdzania odpowiedniej składni separatora dysku (dwukropek).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: f32ee54f88bc4747fd0d8065b0dce06b151d1d9a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475453"
---
# <a name="mitigation-path-colon-checks"></a>Środki zaradcze: sprawdzanie dwukropka ścieżki
Począwszy od aplikacji odnoszących się do .NET Framework 4.6.2, wprowadzono wiele zmian do obsługi poprzednio nieobsługiwanych ścieżek (zarówno pod względem długości, jak i formatu). W szczególności sprawdza poprawność składni separatora dysku (dwukropek).  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokują niektóre ścieżki URI <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> i <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody, które wcześniej były obsługiwane.  
  
## <a name="mitigation"></a>Ograniczanie ryzyka  
 Aby obejść problem z wcześniej akceptowalną ścieżką, która nie jest już obsługiwana przez <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> metody i, można wykonać następujące czynności:  
  
- Ręcznie usuń schemat z adresu URL. Na przykład Usuń `file://` adres URL.  
  
- Przekaż identyfikator URI do <xref:System.Uri> konstruktora i Pobierz wartość <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> właściwości.  
  
- Zrezygnuj z nowej normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> przełącznik na `true` .  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
