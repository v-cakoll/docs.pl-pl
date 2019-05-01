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
ms.openlocfilehash: cf7534cdee5e17d53e95294573023d660135e395
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947696"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="60f82-102">Instrukcje: Otwieranie okna komunikatu</span><span class="sxs-lookup"><span data-stu-id="60f82-102">How to: Open a Message Box</span></span>
<span data-ttu-id="60f82-103">Ten przykład przedstawia sposób otworzyć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="60f82-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="60f82-104">Example</span></span>  
 <span data-ttu-id="60f82-105">Okno komunikatu jest prefabrykowanych modalne okno dialogowe wyświetlane informacje o dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="60f82-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="60f82-106">Okno komunikatu jest otwarty przez wywołanie metody statyczne <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy.</span><span class="sxs-lookup"><span data-stu-id="60f82-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="60f82-107">Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, wiadomości są przekazywane za pomocą parametru ciągu.</span><span class="sxs-lookup"><span data-stu-id="60f82-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="60f82-108">Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> umożliwiają skonfigurowanie sposobu pojawi się okno komunikatu (zobacz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="60f82-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="60f82-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60f82-109">See also</span></span>

- [<span data-ttu-id="60f82-110">Przykładowe MessageBox</span><span class="sxs-lookup"><span data-stu-id="60f82-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
