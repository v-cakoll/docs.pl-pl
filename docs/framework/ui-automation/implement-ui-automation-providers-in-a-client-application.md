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
ms.openlocfilehash: b368ab3bc842fda5a99a64e0220093ebd60698b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105927"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>Implementacja dostawców automatyzacji interfejsu użytkownika w aplikacji klienta
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który pokazuje, jak do implementowania dostawcy automatyzacji interfejsu użytkownika po stronie klienta w obrębie aplikacji.  
  
 Jest to rzadkie scenariusz. W większości przypadków automatyzacji interfejsu użytkownika aplikacja kliencka korzysta z dostawcy po stronie serwera lub dostawcy po stronie klienta, które znajdują się w bibliotece DLL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu implementuje prostego dostawcy okna konsoli. Kod nie ma wszystkie przydatne funkcje, ale jest przeznaczona do zademonstrowania podstawowe kroki tworzenia dostawcy w obrębie kodu klienta i rejestrując ją za pomocą <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Rejestrowanie zestawów dostawcy po stronie klienta](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
