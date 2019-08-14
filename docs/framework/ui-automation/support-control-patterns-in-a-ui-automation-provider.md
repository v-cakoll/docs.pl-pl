---
title: Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: da423af259ac3ef88d5b52d576d3ab5ebb4f916e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971802"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.

W tym temacie przedstawiono sposób implementacji co najmniej jednego wzorca kontroli dla dostawcy automatyzacji interfejsu użytkownika, dzięki czemu aplikacje klienckie mogą manipulować kontrolkami i pobierać z nich dane.

## <a name="support-control-patterns"></a>Obsługa wzorców kontrolek

1. Zaimplementuj odpowiednie interfejsy dla wzorców kontrolek, które element powinien obsługiwać, <xref:System.Windows.Automation.Provider.IInvokeProvider> na <xref:System.Windows.Automation.InvokePattern>przykład.

2. Zwróć obiekt zawierający implementację każdego interfejsu sterowania w implementacji programu<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono implementację <xref:System.Windows.Automation.Provider.ISelectionProvider> dla niestandardowego pola listy o pojedynczym zaznaczeniu. Zwraca trzy właściwości i pobiera aktualnie wybrany element.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono implementację <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> , która zwraca klasę implementującą. <xref:System.Windows.Automation.Provider.ISelectionProvider> Większość formantów pola listy obsługuje inne wzorce, ale w tym przykładzie odwołanie null (`Nothing` w Microsoft Visual Basic .NET) jest zwracane dla wszystkich innych identyfikatorów wzorców.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
