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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="19ce7-102">Ograniczenie: PNG ramki w obiektach ikony</span><span class="sxs-lookup"><span data-stu-id="19ce7-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="19ce7-103">W programie .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda konwertuje pomyślnie ikony PNG ramek do <xref:System.Drawing.Bitmap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="19ce7-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="19ce7-104">W aplikacjach przeznaczonych dla platformy .NET Framework 4.5.2 i wcześniejszych wersjach <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek Jeśli <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="19ce7-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="19ce7-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="19ce7-105">Impact</span></span>  
 <span data-ttu-id="19ce7-106">Ta zmiana wpływa na aplikacje, które są ponownie kompilowana docelową programu .NET Framework 4.6 i implementują specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> który jest zgłaszany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="19ce7-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="19ce7-107">Gdy uruchomiony w ramach programu .NET Framework 4.6, konwersja zakończy się pomyślnie, <xref:System.ArgumentOutOfRangeException> nie jest już zgłoszono i w związku z tym program obsługi wyjątku nie jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="19ce7-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="19ce7-108">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="19ce7-108">Mitigation</span></span>  
 <span data-ttu-id="19ce7-109">Jeśli to zachowanie jest niepożądane, można zachować poprzednie, dodając następujący element do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="19ce7-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="19ce7-110">Jeśli już zawiera plik app.config `AppContextSwitchOverrides` element, nowa wartość powinny zostać scalone z `value` atrybutu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="19ce7-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="19ce7-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19ce7-111">See Also</span></span>  
 [<span data-ttu-id="19ce7-112">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="19ce7-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
