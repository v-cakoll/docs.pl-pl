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
ms.openlocfilehash: ef3d03bee412b97ed88ec76e81ad2fd19a9595eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968946"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera przykładowy kod pokazujący sposób implementacji dostawcy automatyzacji interfejsu użytkownika po stronie klienta w aplikacji.  
  
 Jest to typowy scenariusz. Najczęściej aplikacja klienta automatyzacji interfejsu użytkownika korzysta z dostawców po stronie serwera lub dostawców po stronie klienta, które znajdują się w bibliotece DLL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod implementuje prostego dostawcę dla okna konsoli. Kod nie ma żadnych użytecznych funkcji, ale jest przeznaczony do zademonstrowania podstawowych kroków konfigurowania dostawcy w kodzie klienta i rejestrowania go za pomocą programu <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Rejestrowanie zestawów dostawcy po stronie klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
