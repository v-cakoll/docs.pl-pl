---
title: Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 9f2cba1f602cedf3a13bd909b4dc2f1a7b4ab972
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443123"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>Uzyskiwanie szczegółów atrybutów tekstu mieszanego przy użyciu automatyzacji interfejsu użytkownika
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attribute details from a text range that spans multiple attribute values. A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.  
  
## <a name="example"></a>Przykład  
 The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range where <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> returns a <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> object.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods. For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, the <xref:System.Windows.Automation.AutomationElement> class provides methods for a UI Automation client to access the corresponding native object model.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika — TextPattern](ui-automation-textpattern-overview.md)
- [Dodawanie zawartości do pola tekstowego przy użyciu automatyzacji interfejsu użytkownika](add-content-to-a-text-box-using-ui-automation.md)
- [Znajdowanie i wyróżnianie tekstu przy użyciu automatyzacji interfejsu użytkownika](find-and-highlight-text-using-ui-automation.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Uzyskiwanie atrybutów tekstu przy użyciu automatyzacji interfejsu użytkownika](obtain-text-attributes-using-ui-automation.md)
