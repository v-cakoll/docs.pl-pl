---
title: 'Porady: otwieranie okna komunikatu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: f05190030ed6324917348fa1926abd5385e30f7e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353151"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="a1a35-102">Porady: otwieranie okna komunikatu</span><span class="sxs-lookup"><span data-stu-id="a1a35-102">How to: Open a Message Box</span></span>
<span data-ttu-id="a1a35-103">Ten przykład przedstawia sposób otworzyć okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a1a35-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1a35-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a35-104">Example</span></span>  
 <span data-ttu-id="a1a35-105">Okno komunikatu jest prefabrykowanych modalne okno dialogowe wyświetlane informacje o dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a1a35-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="a1a35-106">Okno komunikatu jest otwarty przez wywołanie metody statyczne <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy.</span><span class="sxs-lookup"><span data-stu-id="a1a35-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="a1a35-107">Gdy <xref:System.Windows.MessageBox.Show%2A> jest wywoływana, wiadomości są przekazywane za pomocą parametru ciągu.</span><span class="sxs-lookup"><span data-stu-id="a1a35-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="a1a35-108">Kilka przeciążeń <xref:System.Windows.MessageBox.Show%2A> umożliwiają skonfigurowanie sposobu pojawi się okno komunikatu (zobacz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="a1a35-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="a1a35-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a35-109">See Also</span></span>  
 [<span data-ttu-id="a1a35-110">Przykładowe MessageBox</span><span class="sxs-lookup"><span data-stu-id="a1a35-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
