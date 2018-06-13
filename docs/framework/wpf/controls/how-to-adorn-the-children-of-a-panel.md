---
title: Jak ozdobić elementy podrzędne panelu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550222"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Jak ozdobić elementy podrzędne panelu
W tym przykładzie pokazano, jak programowo powiązać modułu definiowania układu kodu do podrzędnych określonej <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Przykład  
 Aby powiązać modułu definiowania układu kodu do elementów podrzędnych <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:  
  
1.  Zadeklaruj nową <xref:System.Windows.Documents.AdornerLayer> obiekt i wywołanie `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody do znalezienia warstwy modułu definiowania układu kodu dla elementu, którego elementy podrzędne mają być adorned.  
  
2.  Wyliczenia elementów podrzędnych elementu nadrzędnego i wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu do każdego elementu podrzędnego.  
  
 Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej) do elementów podrzędnych <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać modułu definiowania układu kodu do innego elementu nie jest obecnie obsługiwany.  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)
