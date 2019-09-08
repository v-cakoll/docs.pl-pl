---
title: Środki zaradcze Ramki PNG w obiektach ikon
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a76681cf6efd649fe366a68d956246334975fe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789977"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Środki zaradcze Ramki PNG w obiektach ikon
Począwszy od .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramkami PNG na <xref:System.Drawing.Bitmap> obiekty.  
  
 W aplikacjach przeznaczonych dla .NET Framework 4.5.2 i starszych wersji <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda <xref:System.ArgumentOutOfRangeException> zgłasza wyjątek, jeśli <xref:System.Drawing.Icon> obiekt zawiera ramki PNG.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi <xref:System.ArgumentOutOfRangeException> dla, która jest generowany <xref:System.Drawing.Icon> , gdy obiekt ma ramki PNG. W przypadku uruchamiania w .NET Framework 4,6, konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszane i w związku z tym program obsługi wyjątków nie jest już wywoływany.  
  
### <a name="mitigation"></a>Ograniczenie  
 Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Jeśli plik App. config zawiera `AppContextSwitchOverrides` już element, Nowa wartość powinna być scalona `value` z atrybutem podobnym do tego:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6.md)
