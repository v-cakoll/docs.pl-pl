---
title: Wyłącz RealTimeStylus dla aplikacji WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962493"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="9255e-102">Wyłącz RealTimeStylus dla aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="9255e-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="9255e-103">Windows Presentation Foundation (WPF) zawiera wbudowaną obsługą dla przetwarzania wprowadzanie dotykowe Windows 7. Wsparcie przepływa wejście pióra w czasie rzeczywistym platformy tablet jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, i <xref:System.Windows.UIElement.OnStylusMove%2A> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9255e-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="9255e-104">Windows 7 są także dane wejściowe wielodotyku jako komunikaty okna Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="9255e-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="9255e-105">Te dwa interfejsy API są wzajemnie wykluczających się na tym samym HWND.</span><span class="sxs-lookup"><span data-stu-id="9255e-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="9255e-106">Włączanie touch wejściowych za pośrednictwem platformy tablet (domyślnie dla aplikacji WPF) wyłącza WM_TOUCH wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9255e-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="9255e-107">W rezultacie WM_TOUCH można użyć w celu odbierania komunikatów touch z okna WPF, należy wyłączyć obsługę wbudowanych pióra na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="9255e-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="9255e-108">Ma to zastosowanie w przypadku takich jak okna WPF, obsługujący składnik, który używa WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="9255e-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="9255e-109">Aby wyłączyć WPF nasłuchiwanie wejście pióra, należy usunąć wszelkie tablecie dodano obsługę przez okno WPF.</span><span class="sxs-lookup"><span data-stu-id="9255e-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9255e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9255e-110">Example</span></span>  
 <span data-ttu-id="9255e-111">Poniższy przykład kodu pokazuje, jak usunąć domyślną obsługę platform typu tablet przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="9255e-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9255e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9255e-112">See also</span></span>

- [<span data-ttu-id="9255e-113">Przechwytywanie danych wejściowych z pisaka</span><span class="sxs-lookup"><span data-stu-id="9255e-113">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
