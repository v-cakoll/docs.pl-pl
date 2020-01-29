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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Wyłącz RealTimeStylus dla aplikacji WPF

Windows Presentation Foundation (WPF) ma wbudowaną obsługę przetwarzania danych wejściowych systemu Windows 7. Pomoc techniczna obejmuje dane wejściowe pióra w czasie rzeczywistym platformy tabletu jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>i <xref:System.Windows.UIElement.OnStylusMove%2A> zdarzenia. System Windows 7 udostępnia także wielodotykowe dane wejściowe jako komunikaty okna WM_TOUCH Win32. Te dwa interfejsy API wzajemnie się wykluczają w tym samym kluczu HWND. Włączenie wprowadzania dotykowego za pośrednictwem platformy tabletu (domyślnie dla aplikacji WPF) wyłącza WM_TOUCH komunikatów. W związku z tym, aby używać WM_TOUCH do odbierania komunikatów dotykowych z okna WPF, należy wyłączyć wbudowaną obsługę pióra w WPF. Ma to zastosowanie w scenariuszu, takim jak okno WPF obsługujące składnik, który używa WM_TOUCH.  
  
 Aby wyłączyć program WPF nasłuchuje na wejściu pióra, Usuń każdą obsługę rysownicy dodaną przez okno WPF.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przechwytywanie danych wejściowych z pisaka](intercepting-input-from-the-stylus.md)
