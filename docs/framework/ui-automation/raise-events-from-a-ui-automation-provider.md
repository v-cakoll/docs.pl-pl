---
title: Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 3deb4c6716d83af4b05e15b5b8a4b89e28317406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138700"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>Wywoływanie zdarzeń od dostawcy automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera przykładowy kod, który pokazuje, jak wywołać zdarzenie od dostawcy automatyzacji interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenie jest zgłaszane w implementacji formant niestandardowy przycisk. Implementacja umożliwia automatyzacji interfejsu użytkownika aplikacji klienckiej zasymulować kliknięcia przycisku.  
  
 Aby uniknąć niepotrzebnych przetwarzania przykład sprawdza <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> aby zobaczyć, czy powinien być wywoływany zdarzenia.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
