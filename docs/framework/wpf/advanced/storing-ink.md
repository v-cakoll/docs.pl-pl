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
ms.openlocfilehash: 4089aa7942105c14eb628c75edb7f53ffacfaeb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053378"
---
# <a name="storing-ink"></a>Przechowywanie atramentu
<xref:System.Windows.Ink.StrokeCollection.Save%2A> Metody umożliwiają przechowywanie pisma odręcznego jako pisma odręcznego serializacji formatu (ISF). Konstruktory <xref:System.Windows.Ink.StrokeCollection> klasy umożliwiają odczytywanie danych pisma odręcznego.  
  
## <a name="ink-storage-and-retrieval"></a>Przechowywanie pisma odręcznego i pobieranie  
 W tej sekcji omówiono sposób przechowywania i pobierania pisma odręcznego w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platformy.  
  
 Poniższy przykład wykonuje program obsługi zdarzeń kliknięcia przycisku, który przedstawia użytkownika z oknem dialogowym zapisywania pliku i zapisuje pisma odręcznego z <xref:System.Windows.Controls.InkCanvas> poza do pliku.  
  
 [!code-csharp[DigitalInkTopics#12](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 Poniższy przykład wykonuje program obsługi zdarzeń kliknięcia przycisku, który wyświetli użytkownika z pliku otwarte okno dialogowe i odczytuje pisma odręcznego z pliku do <xref:System.Windows.Controls.InkCanvas> elementu.  
  
 [!code-csharp[DigitalInkTopics#13](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.InkCanvas>
- [Windows Presentation Foundation](../index.md)
