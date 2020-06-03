---
title: 'Środki zaradcze: ramki PNG w obiektach ikon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248898"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="cad77-102">Środki zaradcze: ramki PNG w obiektach ikon</span><span class="sxs-lookup"><span data-stu-id="cad77-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="cad77-103">Począwszy od .NET Framework 4,6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramkami PNG na <xref:System.Drawing.Bitmap> obiekty.</span><span class="sxs-lookup"><span data-stu-id="cad77-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="cad77-104">W aplikacjach przeznaczonych dla .NET Framework 4.5.2 i starszych wersji <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> Metoda zgłasza <xref:System.ArgumentOutOfRangeException> wyjątek, jeśli <xref:System.Drawing.Icon> obiekt zawiera ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="cad77-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="cad77-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="cad77-105">Impact</span></span>  
 <span data-ttu-id="cad77-106">Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem .NET Framework 4,6 i implementowanie specjalnej obsługi dla <xref:System.ArgumentOutOfRangeException> , która jest generowany, gdy <xref:System.Drawing.Icon> obiekt ma ramki PNG.</span><span class="sxs-lookup"><span data-stu-id="cad77-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="cad77-107">W przypadku uruchamiania w .NET Framework 4,6, konwersja kończy się powodzeniem, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszane i w związku z tym program obsługi wyjątków nie jest już wywoływany.</span><span class="sxs-lookup"><span data-stu-id="cad77-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="cad77-108">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="cad77-108">Mitigation</span></span>  
 <span data-ttu-id="cad77-109">Jeśli takie zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do sekcji [ \< > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="cad77-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="cad77-110">Jeśli plik App. config zawiera już `AppContextSwitchOverrides` element, Nowa wartość powinna być scalona z `value` atrybutem podobnym do tego:</span><span class="sxs-lookup"><span data-stu-id="cad77-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="cad77-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cad77-111">See also</span></span>

- [<span data-ttu-id="cad77-112">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="cad77-112">Application compatibility</span></span>](application-compatibility.md)
