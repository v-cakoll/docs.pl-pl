---
title: 'Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy systemu Windows'
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
ms.openlocfilehash: b3cfcc6c2873dfb0eb95cf7950adc6b2bb73e74c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013364"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Instrukcje: zaznaczanie elementu w kontrolce ListView formularzy systemu Windows
W tym przykładzie pokazano, jak programowo wybierz element w formularzach Windows <xref:System.Windows.Forms.ListView> kontroli. Zaznaczenie elementu programowo nie zmieni automatycznie fokus na <xref:System.Windows.Forms.ListView> kontroli. Z tego powodu zwykle także można ustawić elementu, ponieważ skupia się po wybraniu elementu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- A <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` zawierający co najmniej jeden element.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
