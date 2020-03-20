---
title: 'Łagodzenie: Ramki PNG w obiektach ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: d661e45bfbbe5e1c5ca5b7eb123e71aa32a096ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181222"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Łagodzenie: Ramki PNG w obiektach ikon
Począwszy od programu .NET Framework 4.6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramek PNG do <xref:System.Drawing.Bitmap> obiektów.  
  
 W aplikacjach, które są przeznaczone dla .NET Framework 4.5.2 i wcześniejszych wersji, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek, <xref:System.ArgumentOutOfRangeException> jeśli <xref:System.Drawing.Icon> obiekt ma ramki PNG.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana wpływa na aplikacje, które są ponownie kompilowane do celu .NET <xref:System.ArgumentOutOfRangeException> Framework 4.6 i które implementują specjalną obsługę dla tego, który jest generowany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG. Po uruchomieniu w ramach .NET Framework 4.6 <xref:System.ArgumentOutOfRangeException> konwersji zakończy się pomyślnie, nie jest już zgłaszany i dlatego program obsługi wyjątków nie jest już wywoływany.  
  
### <a name="mitigation"></a>Środki zaradcze  
 Jeśli to zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Jeśli plik app.config zawiera `AppContextSwitchOverrides` już element, nowa wartość powinna `value` zostać scalona z atrybutem w ten sposób:  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
