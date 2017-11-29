---
title: "Jak ozdobić elementy podrzędne panelu"
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
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d30e9e5ac15f48dabf983123ba007674a14626d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
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
 [Omówienie modułu definiowania układu kodu](../../../../docs/framework/wpf/controls/adorners-overview.md)
