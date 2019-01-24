---
title: 'Instrukcje: Określ czy hiperłącze jest podkreślone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3199bce25d49bb471fe21735ebb919bbb7f5132c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576965"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Instrukcje: Określ czy hiperłącze jest podkreślone
<xref:System.Windows.Documents.Hyperlink> Obiekt jest element zawartości śródwierszowy przepływ, który pozwala na hosta hiperlinki w dowolnej zawartości. Domyślnie <xref:System.Windows.Documents.Hyperlink> używa <xref:System.Windows.TextDecoration> obiektu, aby wyświetlić podkreślenie. <xref:System.Windows.TextDecoration> obiekty mogą być intensywnie do utworzenia wystąpienia, wydajność, zwłaszcza, jeśli dostępnych jest wiele <xref:System.Windows.Documents.Hyperlink> obiektów. Jeśli wprowadzisz zwiększone użycie <xref:System.Windows.Documents.Hyperlink> elementów, warto wziąć pod uwagę przedstawiający podkreślenie, tylko wtedy, gdy wyzwalanie zdarzenia, takie jak <xref:System.Windows.ContentElement.MouseEnter> zdarzeń.  
  
 W poniższym przykładzie jest dynamiczny podkreślenie dla linku "Mój MSN" — pojawia się tylko, gdy <xref:System.Windows.ContentElement.MouseEnter> zdarzenie jest wyzwalane.  
  
 ![Wyświetlanie właściwości TextDecorations hiperłącza](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Zdefiniowane za pomocą właściwości TextDecorations hiperłącza  
  
## <a name="example"></a>Przykład  
 Ilustruje poniższy przykład kodu znaczników <xref:System.Windows.Documents.Hyperlink> zdefiniowane z lub bez podkreślenie:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Poniższy przykład kodu pokazuje, jak utworzyć podkreślenie dla <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> zdarzenia i usunąć go na <xref:System.Windows.ContentElement.MouseLeave> zdarzeń.  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Tworzenie dekoracji tekstu](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
