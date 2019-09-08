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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="816f7-102">Środki zaradcze Ramki PNG w obiektach ikon</span><span class="sxs-lookup"><span data-stu-id="816f7-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="816f7-103">Począwszy od .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramkami PNG na <xref:System.Drawing.Bitmap> obiekty.</span><span class="sxs-lookup"><span data-stu-id="816f7-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="816f7-104">W aplikacjach przeznaczonych dla .NET Framework 4.5.2 i starszych wersji <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda <xref:System.ArgumentOutOfRangeException> zgłasza wyjątek, jeśli <xref:System.Drawing.Icon> obiekt zawiera ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="816f7-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="816f7-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="816f7-105">Impact</span></span>  
 <span data-ttu-id="816f7-106">Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi <xref:System.ArgumentOutOfRangeException> dla, która jest generowany <xref:System.Drawing.Icon> , gdy obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="816f7-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="816f7-107">W przypadku uruchamiania w .NET Framework 4,6, konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszane i w związku z tym program obsługi wyjątków nie jest już wywoływany.</span><span class="sxs-lookup"><span data-stu-id="816f7-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="816f7-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="816f7-108">Mitigation</span></span>  
 <span data-ttu-id="816f7-109">Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="816f7-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="816f7-110">Jeśli plik App. config zawiera `AppContextSwitchOverrides` już element, Nowa wartość powinna być scalona `value` z atrybutem podobnym do tego:</span><span class="sxs-lookup"><span data-stu-id="816f7-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="816f7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="816f7-111">See also</span></span>

- [<span data-ttu-id="816f7-112">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="816f7-112">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
