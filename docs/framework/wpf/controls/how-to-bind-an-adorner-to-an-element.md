---
title: "Jak powiązać moduł definiowania układu z elementem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3c657cde9da19f8ebc6b6d4d05077ed027781b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Jak powiązać moduł definiowania układu z elementem
W tym przykładzie pokazano, jak programowo powiązać modułu definiowania układu kodu z określonej <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 Aby powiązać modułu definiowania układu kodu do określonego <xref:System.Windows.UIElement>, wykonaj następujące kroki:  
  
1.  Wywołanie `static` — metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> uzyskanie <xref:System.Windows.Documents.AdornerLayer> obiekt do <xref:System.Windows.UIElement> do można adorned. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>przedstawiono w górę drzewa wizualnego, rozpoczynając od określonego **UIElement**i zwraca znajdzie pierwszą warstwę modułu definiowania układu kodu. (Jeśli nie zostaną znalezione nie warstwy modułu definiowania układu kodu, metoda zwraca wartość null.)  
  
2.  Wywołanie <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodę, aby powiązać modułu definiowania układu kodu w miejscu docelowym **UIElement**.  
  
 Poniższy przykład wiąże SimpleCircleAdorner (pokazanym powyżej), aby <xref:System.Windows.Controls.TextBox> o nazwie *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] powiązać modułu definiowania układu kodu do innego elementu nie jest obecnie obsługiwany.  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)
