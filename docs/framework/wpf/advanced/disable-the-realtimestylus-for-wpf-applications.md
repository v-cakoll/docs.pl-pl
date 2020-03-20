---
title: Wyłącz realtimestylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186083"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="2b87d-102">Wyłącz RealTimeStylus dla aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="2b87d-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="2b87d-103">Windows Presentation Foundation (WPF) ma wbudowany w pomocy technicznej do przetwarzania systemu Windows 7 touch input.</span><span class="sxs-lookup"><span data-stu-id="2b87d-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="2b87d-104">Wsparcie jest dostępne za pośrednictwem wejścia rysika w <xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusUp%2A>czasie <xref:System.Windows.UIElement.OnStylusMove%2A> rzeczywistym platformy tabletów jako , i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2b87d-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="2b87d-105">System Windows 7 zapewnia również wprowadzanie wielodotykowe jako komunikaty WM_TOUCH okna w wersji Win32.</span><span class="sxs-lookup"><span data-stu-id="2b87d-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="2b87d-106">Te dwa interfejsy API wzajemnie się wykluczają na tym samym HWND.</span><span class="sxs-lookup"><span data-stu-id="2b87d-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="2b87d-107">Włączenie wprowadzania dotykowego za pośrednictwem platformy tabletu (domyślne dla aplikacji WPF) wyłącza WM_TOUCH komunikatów.</span><span class="sxs-lookup"><span data-stu-id="2b87d-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="2b87d-108">W rezultacie, aby użyć WM_TOUCH do odbierania wiadomości dotykowych z okna WPF, należy wyłączyć wbudowaną obsługę piaka w WPF.</span><span class="sxs-lookup"><span data-stu-id="2b87d-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="2b87d-109">Ma to zastosowanie w scenariuszu, takich jak WPF okno hosting składnika, który używa WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="2b87d-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="2b87d-110">Aby wyłączyć WPF nasłuchiwanie danych wejściowych pisaka, usuń wszystkie wsparcie tabletu dodane przez okno WPF.</span><span class="sxs-lookup"><span data-stu-id="2b87d-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b87d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b87d-111">Example</span></span>  
 <span data-ttu-id="2b87d-112">Poniższy przykładowy kod pokazuje, jak usunąć domyślną obsługę platformy tabletu przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="2b87d-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b87d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b87d-113">See also</span></span>

- [<span data-ttu-id="2b87d-114">Przechwycenie danych z pisaka</span><span class="sxs-lookup"><span data-stu-id="2b87d-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
