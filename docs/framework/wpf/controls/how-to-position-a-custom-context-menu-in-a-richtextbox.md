---
title: 'Instrukcje: Ustawianie położenia menu kontekstowego w kontrolce RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770828"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Instrukcje: Ustawianie położenia menu kontekstowego w kontrolce RichTextBox
W tym przykładzie pokazano, jak położenie menu kontekstowego dla <xref:System.Windows.Controls.RichTextBox>.  
  
 Podczas implementacji menu kontekstowego dla **RichTextBox**, jesteś odpowiedzialny za obsługę położenie menu kontekstowego.  Domyślnie menu kontekstowego jest otwarty w środku **RichTextBox**.  
  
## <a name="example"></a>Przykład  
 Aby zastąpić domyślne zachowanie umieszczania, dodanie detektora <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> zdarzeń.  Poniższy przykład pokazuje, jak to zrobić programowo.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano implementację odpowiednich <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> odbiornik zdarzeń.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Zobacz także

- [RichTextBox — omówienie](richtextbox-overview.md)
- [TextBox — omówienie](textbox-overview.md)
