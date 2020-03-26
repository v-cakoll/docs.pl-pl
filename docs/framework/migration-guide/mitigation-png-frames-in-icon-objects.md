---
title: 'Łagodzenie: Ramki PNG w obiektach ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248898"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="f5c64-102">Łagodzenie: Ramki PNG w obiektach ikon</span><span class="sxs-lookup"><span data-stu-id="f5c64-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="f5c64-103">Począwszy od programu .NET Framework 4.6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramek PNG do <xref:System.Drawing.Bitmap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f5c64-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="f5c64-104">W aplikacjach, które są przeznaczone dla .NET Framework 4.5.2 i wcześniejszych wersji, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek, <xref:System.ArgumentOutOfRangeException> jeśli <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="f5c64-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f5c64-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="f5c64-105">Impact</span></span>  
 <span data-ttu-id="f5c64-106">Ta zmiana wpływa na aplikacje, które są ponownie kompilowane do celu .NET <xref:System.ArgumentOutOfRangeException> Framework 4.6 i które implementują specjalną obsługę dla tego, który jest generowany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="f5c64-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="f5c64-107">Po uruchomieniu w ramach .NET Framework 4.6 <xref:System.ArgumentOutOfRangeException> konwersji zakończy się pomyślnie, nie jest już zgłaszany i dlatego program obsługi wyjątków nie jest już wywoływany.</span><span class="sxs-lookup"><span data-stu-id="f5c64-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="f5c64-108">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="f5c64-108">Mitigation</span></span>  
 <span data-ttu-id="f5c64-109">Jeśli to zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="f5c64-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="f5c64-110">Jeśli plik app.config zawiera `AppContextSwitchOverrides` już element, nowa wartość powinna `value` zostać scalona z atrybutem w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="f5c64-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="f5c64-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5c64-111">See also</span></span>

- [<span data-ttu-id="f5c64-112">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="f5c64-112">Application compatibility</span></span>](application-compatibility.md)
