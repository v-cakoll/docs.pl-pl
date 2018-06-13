---
title: 'Porady: zaznaczanie elementu w formancie ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532824"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Porady: zaznaczanie elementu w formancie ListView formularzy systemu Windows
W tym przykładzie pokazano, jak programowo wybierz element w formularzach systemu Windows <xref:System.Windows.Forms.ListView> formantu. Programowy Wybór elementu nie zmienia się automatycznie fokusu <xref:System.Windows.Forms.ListView> formantu. Z tego powodu będzie zwykle również chcesz ustawić element zgodnie z fokusem, gdy zaznaczenie elementu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` zawiera co najmniej jeden element.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
