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
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="2648b-102">Instrukcje: Otwieranie okna komunikatu</span><span class="sxs-lookup"><span data-stu-id="2648b-102">How to: Open a Message Box</span></span>
<span data-ttu-id="2648b-103">Ten przykład pokazuje, jak otworzyć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="2648b-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2648b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2648b-104">Example</span></span>  
 <span data-ttu-id="2648b-105">Okno komunikatu to prefabrykowane modalne okno dialogowe umożliwiające wyświetlanie informacji dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2648b-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="2648b-106">Okno komunikatu jest otwierane przez wywołanie statycznej metody <xref:System.Windows.MessageBox.Show%2A> klasy <xref:System.Windows.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="2648b-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="2648b-107">Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, komunikat jest przesyłany przy użyciu parametru ciągu.</span><span class="sxs-lookup"><span data-stu-id="2648b-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="2648b-108">Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> umożliwia skonfigurowanie sposobu wyświetlania okna komunikatu (zobacz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="2648b-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="2648b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2648b-109">See also</span></span>

- [<span data-ttu-id="2648b-110">MessageBox — przykład</span><span class="sxs-lookup"><span data-stu-id="2648b-110">MessageBox Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
