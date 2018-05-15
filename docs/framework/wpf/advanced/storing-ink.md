---
title: Przechowywanie atramentu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: d3d33be5e8b5cf9dd7e32a52dfc258aa934c5c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="storing-ink"></a><span data-ttu-id="34976-102">Przechowywanie atramentu</span><span class="sxs-lookup"><span data-stu-id="34976-102">Storing Ink</span></span>
<span data-ttu-id="34976-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody zapewniają obsługę przechowywania odręcznego jako pismo odręczne serializacji formatu (ISF).</span><span class="sxs-lookup"><span data-stu-id="34976-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="34976-104">Konstruktory <xref:System.Windows.Ink.StrokeCollection> klasy zapewniają obsługę do odczytywania danych odręczne.</span><span class="sxs-lookup"><span data-stu-id="34976-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="34976-105">Odręczne przechowywanie i pobieranie</span><span class="sxs-lookup"><span data-stu-id="34976-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="34976-106">W tej sekcji omówiono sposób przechowywania i pobierania pismo odręczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.</span><span class="sxs-lookup"><span data-stu-id="34976-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="34976-107">Poniższy przykład implementuje obsługi zdarzeń kliknięcia przycisku, który wyświetla użytkownikowi okno dialogowe Zapisz plik i zapisuje pismo odręczne z <xref:System.Windows.Controls.InkCanvas> poza do pliku.</span><span class="sxs-lookup"><span data-stu-id="34976-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="34976-108">Poniższy przykład implementuje obsługi zdarzeń kliknięcia przycisku, który wyświetla użytkownikowi okno dialogowe Otwieranie pliku i odczytuje odręczne z pliku do <xref:System.Windows.Controls.InkCanvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="34976-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="34976-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34976-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="34976-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="34976-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
