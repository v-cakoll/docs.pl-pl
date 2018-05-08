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
# <a name="storing-ink"></a>Przechowywanie atramentu
<xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody zapewniają obsługę przechowywania odręcznego jako pismo odręczne serializacji formatu (ISF). Konstruktory <xref:System.Windows.Ink.StrokeCollection> klasy zapewniają obsługę do odczytywania danych odręczne.  
  
## <a name="ink-storage-and-retrieval"></a>Odręczne przechowywanie i pobieranie  
 W tej sekcji omówiono sposób przechowywania i pobierania pismo odręczne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.  
  
 Poniższy przykład implementuje obsługi zdarzeń kliknięcia przycisku, który wyświetla użytkownikowi okno dialogowe Zapisz plik i zapisuje pismo odręczne z <xref:System.Windows.Controls.InkCanvas> poza do pliku.  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Poniższy przykład implementuje obsługi zdarzeń kliknięcia przycisku, który wyświetla użytkownikowi okno dialogowe Otwieranie pliku i odczytuje odręczne z pliku do <xref:System.Windows.Controls.InkCanvas> elementu.  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)
