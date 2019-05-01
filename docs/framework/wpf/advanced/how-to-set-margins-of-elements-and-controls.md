---
title: 'Instrukcje: Ustawianie marginesów elementów i kontrolek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 3263810806b6b4bbec15eadfd1f1da3a57d12698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052368"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Instrukcje: Ustawianie marginesów elementów i kontrolek
W tym przykładzie przedstawiono sposób ustawiania <xref:System.Windows.FrameworkElement.Margin%2A> właściwości, zmieniając wszelkie istniejące wartości właściwości dla marginesu w związanym z kodem. <xref:System.Windows.FrameworkElement.Margin%2A> Właściwość jest właściwością <xref:System.Windows.FrameworkElement> podstawowy element i w związku z tym jest dziedziczona przez szereg formantów i innych elementów.  
  
 W tym przykładzie są zapisywane [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], za pomocą kodu powiązanego pliku, który [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odwołuje się do. Związane z kodem jest wyświetlany w obu C# i wersji programu Microsoft Visual Basic.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
