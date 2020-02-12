---
title: 'Instrukcje: Otwieranie okna komunikatu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123730"
---
# <a name="how-to-open-a-message-box"></a>Instrukcje: Otwieranie okna komunikatu
Ten przykład pokazuje, jak otworzyć okno komunikatu.  
  
## <a name="example"></a>Przykład  
 Okno komunikatu to prefabrykowane modalne okno dialogowe umożliwiające wyświetlanie informacji dla użytkowników. Okno komunikatu jest otwierane przez wywołanie statycznej metody <xref:System.Windows.MessageBox.Show%2A> klasy <xref:System.Windows.MessageBox>. Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, komunikat jest przesyłany przy użyciu parametru ciągu. Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> umożliwia skonfigurowanie sposobu wyświetlania okna komunikatu (zobacz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Zobacz też

- [MessageBox — przykład](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
