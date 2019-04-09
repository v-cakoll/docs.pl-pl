---
title: 'Środki zaradcze: PNG ramki w obiektach ikony'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d77524e567ba55f7cd9222d690fcee25d3f20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102872"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="c4631-102">Środki zaradcze: PNG ramki w obiektach ikony</span><span class="sxs-lookup"><span data-stu-id="c4631-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="c4631-103">Począwszy od programu .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda konwertuje pomyślnie ikon PNG ramek do <xref:System.Drawing.Bitmap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c4631-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="c4631-104">W aplikacjach przeznaczonych dla platformy .NET Framework 4.5.2 i wcześniejszymi wersjami <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek <xref:System.ArgumentOutOfRangeException> wyjątek Jeśli <xref:System.Drawing.Icon> obiekt ma ramek PNG.</span><span class="sxs-lookup"><span data-stu-id="c4631-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c4631-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="c4631-105">Impact</span></span>  
 <span data-ttu-id="c4631-106">Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem programu .NET Framework 4.6 i implementują specjalna obsługa <xref:System.ArgumentOutOfRangeException> , jest generowany, gdy <xref:System.Drawing.Icon> obiekt ma ramek PNG.</span><span class="sxs-lookup"><span data-stu-id="c4631-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="c4631-107">Podczas uruchamiania w .NET Framework 4.6, konwersja zakończy się pomyślnie, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszany, i w związku z tym program obsługi wyjątku nie jest już jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c4631-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="c4631-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="c4631-108">Mitigation</span></span>  
 <span data-ttu-id="c4631-109">Jeśli to zachowanie jest niepożądany, można zachować poprzednie zachowanie, dodając następujący element do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="c4631-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="c4631-110">Jeśli już zawiera plik app.config `AppContextSwitchOverrides` elementu, nowa wartość ma zostać scalona z `value` atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c4631-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4631-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4631-111">See also</span></span>

- [<span data-ttu-id="c4631-112">Zmiany przekierowania</span><span class="sxs-lookup"><span data-stu-id="c4631-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
