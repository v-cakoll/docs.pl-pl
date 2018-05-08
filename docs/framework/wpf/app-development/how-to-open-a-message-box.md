---
title: 'Porady: Otwórz okno komunikatu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: dd79d69c9b1b54c5158b58ee2f1675e7d11a386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-message-box"></a>Porady: Otwórz okno komunikatu
Ten przykład przedstawia sposób otworzyć okno komunikatu.  
  
## <a name="example"></a>Przykład  
 Okno komunikatu jest prefabrykowanych modalne okno dialogowe wyświetlane informacje o dla użytkowników. Okno komunikatu jest otwarty przez wywołanie metody statycznych <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy. Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, zostanie przetworzona za pomocą parametru ciągu. Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> pozwalają skonfigurować wygląd pola wiadomości (zobacz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowy element MessageBox](http://go.microsoft.com/fwlink/?LinkID=160023)
