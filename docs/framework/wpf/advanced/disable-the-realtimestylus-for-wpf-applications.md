---
title: Wyłącz RealTimeStylus dla aplikacji WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: acae177e1c49a6a1161bcf48f8e2e8ac1bfe13b8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991844"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Wyłącz RealTimeStylus dla aplikacji WPF
Windows Presentation Foundation (WPF) ma wbudowaną obsługę przetwarzania danych wejściowych systemu Windows 7. Pomoc techniczna obejmuje wprowadzanie piórem w czasie rzeczywistym na platformie tabletu jako <xref:System.Windows.UIElement.OnStylusDown%2A>zdarzenia <xref:System.Windows.UIElement.OnStylusUp%2A>, i <xref:System.Windows.UIElement.OnStylusMove%2A> . System Windows 7 udostępnia także wielodotykowe dane wejściowe jako komunikaty okna WM_TOUCH Win32. Te dwa interfejsy API wzajemnie się wykluczają w tym samym kluczu HWND. Włączenie wprowadzania dotykowego za pośrednictwem platformy tabletu (domyślnie dla aplikacji WPF) powoduje wyłączenie komunikatów WM_TOUCH. W związku z tym, aby używać WM_TOUCH do odbierania komunikatów dotykowych z okna WPF, należy wyłączyć wbudowaną obsługę pióra w WPF. Ma to zastosowanie w scenariuszu, takim jak okno WPF obsługujące składnik korzystający z WM_TOUCH.  
  
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
