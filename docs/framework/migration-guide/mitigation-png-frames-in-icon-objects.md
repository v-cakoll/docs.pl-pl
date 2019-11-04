---
title: 'Środki zaradcze: ramki PNG w obiektach ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 1a4ae0c069a4cd6d53bce77e64822ebf3fbb5361
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457868"
---
# <a name="mitigation-png-frames-in-icon-objects"></a>Środki zaradcze: ramki PNG w obiektach ikon
Począwszy od .NET Framework 4,6, Metoda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> pomyślnie konwertuje ikony z ramkami PNG na obiekty <xref:System.Drawing.Bitmap>.  
  
 W aplikacjach, które są przeznaczone dla .NET Framework 4.5.2 i starszych wersji, Metoda <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> zgłasza wyjątek <xref:System.ArgumentOutOfRangeException>, jeśli obiekt <xref:System.Drawing.Icon> ma ramki PNG.  
  
## <a name="impact"></a>Wpływ  
 Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException>, który jest generowany, gdy obiekt <xref:System.Drawing.Icon> ma ramki PNG. W przypadku uruchamiania w .NET Framework 4,6 konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszana i w związku z tym program obsługi wyjątków nie jest już wywoływany.  
  
### <a name="mitigation"></a>Ograniczenie  
 Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) pliku App. config:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 Jeśli plik App. config zawiera już element `AppContextSwitchOverrides`, Nowa wartość powinna zostać scalona z atrybutem `value` podobnym do tego:  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
