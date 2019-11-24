---
title: Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 09b33b78ef8f0b62ef4f1e24c56faae783f1e8dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435471"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic contains example code that shows how to implement a client-side UI Automation provider within an application.  
  
 This is an uncommon scenario. Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.  
  
## <a name="example"></a>Przykład  
 The following example code implements a simple provider for a console window. The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](ui-automation-providers-overview.md)
- [Rejestrowanie zestawów dostawcy po stronie klienta](register-a-client-side-provider-assembly.md)
- [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](create-a-client-side-ui-automation-provider.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta](client-side-ui-automation-provider-implementation.md)
