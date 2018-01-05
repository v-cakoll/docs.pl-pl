---
title: "Porady: Otwórz okno komunikatu"
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
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1754fa190a638c1a200805e339f91bd582d27c4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-message-box"></a>Porady: Otwórz okno komunikatu
Ten przykład przedstawia sposób otworzyć okno komunikatu.  
  
## <a name="example"></a>Przykład  
 Okno komunikatu jest prefabrykowanych modalne okno dialogowe wyświetlane informacje o dla użytkowników. Okno komunikatu jest otwarty przez wywołanie metody statycznych <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy. Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, zostanie przetworzona za pomocą parametru ciągu. Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> pozwalają skonfigurować wygląd pola wiadomości (zobacz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowy element MessageBox](http://go.microsoft.com/fwlink/?LinkID=160023)
