---
title: Wyłącz Obiekt RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737937"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="8e8d3-102">Wyłącz RealTimeStylus dla aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="8e8d3-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="8e8d3-103">Windows Presentation Foundation (WPF) ma wbudowaną obsługę przetwarzania danych wejściowych systemu Windows 7.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="8e8d3-104">Pomoc techniczna obejmuje dane wejściowe pióra w czasie rzeczywistym platformy tabletu jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>i <xref:System.Windows.UIElement.OnStylusMove%2A> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="8e8d3-105">System Windows 7 udostępnia także wielodotykowe dane wejściowe jako komunikaty okna WM_TOUCH Win32.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="8e8d3-106">Te dwa interfejsy API wzajemnie się wykluczają w tym samym kluczu HWND.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="8e8d3-107">Włączenie wprowadzania dotykowego za pośrednictwem platformy tabletu (domyślnie dla aplikacji WPF) wyłącza WM_TOUCH komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="8e8d3-108">W związku z tym, aby używać WM_TOUCH do odbierania komunikatów dotykowych z okna WPF, należy wyłączyć wbudowaną obsługę pióra w WPF.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="8e8d3-109">Ma to zastosowanie w scenariuszu, takim jak okno WPF obsługujące składnik, który używa WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="8e8d3-110">Aby wyłączyć program WPF nasłuchuje na wejściu pióra, Usuń każdą obsługę rysownicy dodaną przez okno WPF.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e8d3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e8d3-111">Example</span></span>  
 <span data-ttu-id="8e8d3-112">Poniższy przykładowy kod pokazuje, jak usunąć domyślną obsługę platformy tabletu przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="8e8d3-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```csharp  
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
  
## <a name="see-also"></a><span data-ttu-id="8e8d3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e8d3-113">See also</span></span>

- [<span data-ttu-id="8e8d3-114">Przechwytywanie danych wejściowych z pisaka</span><span class="sxs-lookup"><span data-stu-id="8e8d3-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
