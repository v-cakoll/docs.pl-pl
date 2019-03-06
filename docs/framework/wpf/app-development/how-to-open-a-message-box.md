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
ms.openlocfilehash: fa371b62c78a08e25de815fa44360230b6156008
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369607"
---
# <a name="how-to-open-a-message-box"></a>Instrukcje: Otwieranie okna komunikatu
Ten przykład przedstawia sposób otworzyć okno komunikatu.  
  
## <a name="example"></a>Przykład  
 Okno komunikatu jest prefabrykowanych modalne okno dialogowe wyświetlane informacje o dla użytkowników. Okno komunikatu jest otwarty przez wywołanie metody statyczne <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy. Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, wiadomości są przekazywane za pomocą parametru ciągu. Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> umożliwiają skonfigurowanie sposobu pojawi się okno komunikatu (zobacz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Zobacz także
- [Przykładowe MessageBox](https://go.microsoft.com/fwlink/?LinkID=160023)
