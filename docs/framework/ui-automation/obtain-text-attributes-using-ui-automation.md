---
title: Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5f1e5cfbf72ebce605c7f08ae944dc3d235dcf7a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587880"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak używać [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] na uzyskiwanie atrybutów tekstu z zakresu tekstu. Zakres tekstu może odpowiadać w bieżącej lokalizacji karetki (lub zdegenerowanym zaznaczenia) w dokumencie, wyboru ciągłego, tekstu, zbiór zaznaczenia tekstu rozłączne lub całej zawartości tekstowej dokumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób uzyskiwania <xref:System.Windows.Automation.TextPattern.FontNameAttribute> z zakresu tekstu.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern> — Wzorzec kontrolki, w połączeniu z sekcją <xref:System.Windows.Automation.Text.TextPatternRange> klasy, obsługuje podstawowe atrybuty, właściwości i metody. Dla funkcji specyficznej dla kontroli, która nie jest obsługiwana przez <xref:System.Windows.Automation.TextPattern> lub <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, klasa dostarcza metody dla klientów automatyzacji interfejsu użytkownika dostępu odpowiedni model obiektów natywnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika — TextPattern](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
