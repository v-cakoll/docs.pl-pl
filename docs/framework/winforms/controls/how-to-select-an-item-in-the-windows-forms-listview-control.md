---
title: Wybierz element w kontrolce ListView
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
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743235"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Porady: zaznaczanie elementu w formancie ListView formularzy systemu Windows
W tym przykładzie pokazano, jak programowo wybrać element w kontrolce <xref:System.Windows.Forms.ListView> Windows Forms. Zaznaczanie elementu programowo nie powoduje automatycznego zmiany fokusu w kontrolce <xref:System.Windows.Forms.ListView>. Z tego powodu zazwyczaj trzeba ustawić element jako skoncentrowany podczas wybierania elementu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.ListView> o nazwie `listView1`, która zawiera co najmniej jeden element.  
  
- Odwołania do przestrzeni nazw <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
