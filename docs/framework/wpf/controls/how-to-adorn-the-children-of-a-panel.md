---
title: 'Instrukcje: Zdób elementy podrzędne panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 9f840180edf55c3e10e6859dfc2b9f4b6495b878
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358200"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Instrukcje: Zdób elementy podrzędne panelu
W tym przykładzie pokazano, jak programowo powiązać moduł definiowania układu z element podrzędny określonego <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Przykład  
 Aby powiązać moduł definiowania układu z elementami podrzędnymi <xref:System.Windows.Controls.Panel>, wykonaj następujące kroki:  
  
1.  Zadeklaruj nowy <xref:System.Windows.Documents.AdornerLayer> obiektu, a następnie wywołać `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody do znalezienia warstwy moduł definiowania układu dla elementu, którego elementy podrzędne, które mają być powiązany.  
  
2.  Wyliczyć elementy podrzędne elementu nadrzędnego, a wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać moduł definiowania układu z każdego elementu podrzędnego.  
  
 Poniższy przykład tworzy powiązanie SimpleCircleAdorner (pokazany powyżej), z elementami podrzędnymi <xref:System.Windows.Controls.StackPanel> o nazwie *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Za pomocą [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać moduł definiowania układu z innego elementu nie jest obecnie obsługiwane.  
  
## <a name="see-also"></a>Zobacz także
- [Moduły indeksowania układu — omówienie](adorners-overview.md)
