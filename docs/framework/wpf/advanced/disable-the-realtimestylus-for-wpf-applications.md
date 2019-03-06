---
title: Wyłącz RealTimeStylus dla aplikacji WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 6af7ff3addfe2673ab73ff0f977770f89c6234bb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371143"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Wyłącz RealTimeStylus dla aplikacji WPF
Windows Presentation Foundation (WPF) zawiera wbudowaną obsługą dla przetwarzania wprowadzanie dotykowe Windows 7. Wsparcie przepływa wejście pióra w czasie rzeczywistym platformy tablet jako <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, i <xref:System.Windows.UIElement.OnStylusMove%2A> zdarzenia. Windows 7 są także dane wejściowe wielodotyku jako komunikaty okna Win32 WM_TOUCH. Te dwa interfejsy API są wzajemnie wykluczających się na tym samym HWND. Włączanie touch wejściowych za pośrednictwem platformy tablet (domyślnie dla aplikacji WPF) wyłącza WM_TOUCH wiadomości. W rezultacie WM_TOUCH można użyć w celu odbierania komunikatów touch z okna WPF, należy wyłączyć obsługę wbudowanych pióra na platformie WPF. Ma to zastosowanie w przypadku takich jak okna WPF, obsługujący składnik, który używa WM_TOUCH.  
  
 Aby wyłączyć WPF nasłuchiwanie wejście pióra, należy usunąć wszelkie tablecie dodano obsługę przez okno WPF.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak usunąć domyślną obsługę platform typu tablet przy użyciu odbicia.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Przechwytywanie danych wejściowych z pisaka](intercepting-input-from-the-stylus.md)
