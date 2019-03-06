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
ms.openlocfilehash: aec89286cfac9b0a315dc2d00135543511b2d1ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353962"
---
# <a name="storing-ink"></a><span data-ttu-id="270f9-102">Przechowywanie atramentu</span><span class="sxs-lookup"><span data-stu-id="270f9-102">Storing Ink</span></span>
<span data-ttu-id="270f9-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody umożliwiają przechowywanie pisma odręcznego jako pisma odręcznego serializacji formatu (ISF).</span><span class="sxs-lookup"><span data-stu-id="270f9-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="270f9-104">Konstruktory <xref:System.Windows.Ink.StrokeCollection> klasy umożliwiają odczytywanie danych pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="270f9-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="270f9-105">Przechowywanie pisma odręcznego i pobieranie</span><span class="sxs-lookup"><span data-stu-id="270f9-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="270f9-106">W tej sekcji omówiono sposób przechowywania i pobierania pisma odręcznego w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.</span><span class="sxs-lookup"><span data-stu-id="270f9-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="270f9-107">Poniższy przykład wykonuje program obsługi zdarzeń kliknięcia przycisku, który przedstawia użytkownika z oknem dialogowym zapisywania pliku i zapisuje pisma odręcznego z <xref:System.Windows.Controls.InkCanvas> poza do pliku.</span><span class="sxs-lookup"><span data-stu-id="270f9-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="270f9-108">Poniższy przykład wykonuje program obsługi zdarzeń kliknięcia przycisku, który wyświetli użytkownika z pliku otwarte okno dialogowe i odczytuje pisma odręcznego z pliku do <xref:System.Windows.Controls.InkCanvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="270f9-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="270f9-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="270f9-109">See also</span></span>
- <xref:System.Windows.Controls.InkCanvas>
- [<span data-ttu-id="270f9-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="270f9-110">Windows Presentation Foundation</span></span>](../index.md)
