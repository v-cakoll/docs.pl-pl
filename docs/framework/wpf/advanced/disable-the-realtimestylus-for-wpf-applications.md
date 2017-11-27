---
title: "Wyłącz RealTimeStylus dla aplikacji WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01a4d8f6d98eb341021442d9b7964816dd673374
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="9cc78-102">Wyłącz RealTimeStylus dla aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="9cc78-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="9cc78-103">Windows Presentation Foundation (WPF) zawiera wbudowaną obsługą przetwarzania wprowadzania dotykowego systemu Windows 7. Obsługę jest dostarczany za pośrednictwem wprowadzania danych w czasie rzeczywistym piórem platformy tablet jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, i <xref:System.Windows.UIElement.OnStylusMove%2A> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9cc78-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="9cc78-104">Windows 7 także wielodotyku danych wejściowych jako komunikaty okna Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="9cc78-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="9cc78-105">Te dwa interfejsy API wzajemnie się wykluczają na tym samym HWND.</span><span class="sxs-lookup"><span data-stu-id="9cc78-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="9cc78-106">Wprowadzania dotykowego włączenie za pośrednictwem platformy tablet (wartość domyślna dla aplikacji WPF) wyłącza WM_TOUCH wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9cc78-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="9cc78-107">W związku z tym na potrzeby odbierania komunikatów touch z okna WPF WM_TOUCH, należy wyłączyć obsługę wbudowanych Pióro na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="9cc78-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="9cc78-108">Ma to zastosowanie w przypadku takich jak obsługującym składnik, który używa WM_TOUCH okna WPF.</span><span class="sxs-lookup"><span data-stu-id="9cc78-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="9cc78-109">Aby wyłączyć nasłuchiwanie wprowadzania danych piórem WPF, usuń wszelkie wsparcie tablet dodane przez okno WPF.</span><span class="sxs-lookup"><span data-stu-id="9cc78-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc78-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cc78-110">Example</span></span>  
 <span data-ttu-id="9cc78-111">Następujący przykładowy kod przedstawia sposób usuwania domyślnego typu tablet platformy obsługiwane przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="9cc78-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9cc78-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cc78-112">See Also</span></span>  
 [<span data-ttu-id="9cc78-113">Przechwycenia danych wejściowych z pióra</span><span class="sxs-lookup"><span data-stu-id="9cc78-113">Intercepting Input from the Stylus</span></span>](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)
