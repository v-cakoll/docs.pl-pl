---
title: 'Środki zaradcze: ramki PNG w obiektach ikon'
description: Dowiedz się, jak skonfigurować zachowanie ramek PNG w obiektach ikon, jeśli nowe zachowanie zawarte w .NET Framework 4,6 i nowszych jest niepożądane.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: b7ba2951a38ee2d1c7a9b1fc45c5a81d24986a85
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475440"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="d4530-103">Środki zaradcze: ramki PNG w obiektach ikon</span><span class="sxs-lookup"><span data-stu-id="d4530-103">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="d4530-104">Począwszy od .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramkami PNG na <xref:System.Drawing.Bitmap> obiekty.</span><span class="sxs-lookup"><span data-stu-id="d4530-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="d4530-105">W aplikacjach przeznaczonych dla .NET Framework 4.5.2 i starszych wersji <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek, jeśli <xref:System.Drawing.Icon> obiekt zawiera ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="d4530-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d4530-106">Wpływ</span><span class="sxs-lookup"><span data-stu-id="d4530-106">Impact</span></span>  
 <span data-ttu-id="d4530-107">Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> , która jest generowany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="d4530-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="d4530-108">W przypadku uruchamiania w .NET Framework 4,6, konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszane i w związku z tym program obsługi wyjątków nie jest już wywoływany.</span><span class="sxs-lookup"><span data-stu-id="d4530-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="d4530-109">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="d4530-109">Mitigation</span></span>  
 <span data-ttu-id="d4530-110">Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="d4530-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="d4530-111">Jeśli plik app.config zawiera już `AppContextSwitchOverrides` element, Nowa wartość powinna być scalona z `value` atrybutem podobnym do tego:</span><span class="sxs-lookup"><span data-stu-id="d4530-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="d4530-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4530-112">See also</span></span>

- [<span data-ttu-id="d4530-113">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="d4530-113">Application compatibility</span></span>](application-compatibility.md)
