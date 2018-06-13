---
title: 'Ograniczenie: PNG ramki w obiektach ikony'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3ee5cc03f684acf103c96ecd14387f119bf0bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387929"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Ograniczenie: PNG ramki w obiektach ikony
W programie .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda konwertuje pomyślnie ikony PNG ramek do <xref:System.Drawing.Bitmap> obiektów.  
  
 W aplikacjach przeznaczonych dla platformy .NET Framework 4.5.2 i wcześniejszych wersjach <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek Jeśli <xref:System.Drawing.Icon> obiekt ma ramki PNG.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana wpływa na aplikacje, które są ponownie kompilowana docelową programu .NET Framework 4.6 i implementują specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> który jest zgłaszany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG. Gdy uruchomiony w ramach programu .NET Framework 4.6, konwersja zakończy się pomyślnie, <xref:System.ArgumentOutOfRangeException> nie jest już zgłoszono i w związku z tym program obsługi wyjątku nie jest wywoływany.  
  
### <a name="mitigation"></a>Ograniczenie  
 Jeśli to zachowanie jest niepożądane, można zachować poprzednie, dodając następujący element do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Jeśli już zawiera plik app.config `AppContextSwitchOverrides` element, nowa wartość powinny zostać scalone z `value` atrybutu w następujący sposób:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
