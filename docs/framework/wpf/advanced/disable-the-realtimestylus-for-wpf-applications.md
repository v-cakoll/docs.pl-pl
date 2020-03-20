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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Wyłącz RealTimeStylus dla aplikacji WPF

Windows Presentation Foundation (WPF) ma wbudowany w pomocy technicznej do przetwarzania systemu Windows 7 touch input. Wsparcie jest dostępne za pośrednictwem wejścia rysika w <xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusUp%2A>czasie <xref:System.Windows.UIElement.OnStylusMove%2A> rzeczywistym platformy tabletów jako , i zdarzeń. System Windows 7 zapewnia również wprowadzanie wielodotykowe jako komunikaty WM_TOUCH okna w wersji Win32. Te dwa interfejsy API wzajemnie się wykluczają na tym samym HWND. Włączenie wprowadzania dotykowego za pośrednictwem platformy tabletu (domyślne dla aplikacji WPF) wyłącza WM_TOUCH komunikatów. W rezultacie, aby użyć WM_TOUCH do odbierania wiadomości dotykowych z okna WPF, należy wyłączyć wbudowaną obsługę piaka w WPF. Ma to zastosowanie w scenariuszu, takich jak WPF okno hosting składnika, który używa WM_TOUCH.  
  
 Aby wyłączyć WPF nasłuchiwanie danych wejściowych pisaka, usuń wszystkie wsparcie tabletu dodane przez okno WPF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod pokazuje, jak usunąć domyślną obsługę platformy tabletu przy użyciu odbicia.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Przechwycenie danych z pisaka](intercepting-input-from-the-stylus.md)
