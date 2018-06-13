---
title: Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f84f31f2a2022d42bc62d0a72d4f44282e60753b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403773"
---
# <a name="return-properties-from-a-ui-automation-provider"></a>Zwracanie właściwości od dostawcy automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który pokazuje, jak dostawcy automatyzacji interfejsu użytkownika może zwracać element właściwości dla aplikacji klienckich.  
  
 Dla każdej właściwości, nie obsługuje jawnie dostawcy musi zwracać `null` (`Nothing` w języku Visual Basic). Gwarantuje to, że [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] próbuje uzyskać właściwości z innego źródła, takiego jak dostawca okno hosta.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
