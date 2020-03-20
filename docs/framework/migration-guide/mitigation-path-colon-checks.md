---
title: 'Łagodzenie: Kontrola dwukropek ścieżki'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181244"
---
# <a name="mitigation-path-colon-checks"></a>Łagodzenie: Kontrola dwukropek ścieżki
Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.2, wprowadzono szereg zmian w celu obsługi wcześniej nieobsługiwał ścieżek (zarówno pod względem długości i formatu). W szczególności, kontrole prawidłowej składni separatora dysku (dwukropek) zostały bardziej poprawne.  
  
## <a name="impact"></a>Wpływ  
 Te zmiany blokują niektóre <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ścieżki <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> URI i metody wcześniej obsługiwane.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Aby obejść problem wcześniej akceptowalnej ścieżki, która nie <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> jest <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> już obsługiwana przez metody i, można wykonać następujące czynności:  
  
- Ręcznie usuń schemat z adresu URL. Na przykład `file://` usuń z adresu URL.  
  
- Przekaż identyfikator URI <xref:System.Uri> do konstruktora i <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> pobrać wartość właściwości.  
  
- Zrezygnuj z normalizacji `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> nowej `true`ścieżki, ustawiając przełącznik na .  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
