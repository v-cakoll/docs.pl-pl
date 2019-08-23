---
title: Rozpoznawanie pisma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956532"
---
# <a name="handwriting-recognition"></a>Rozpoznawanie pisma
W tej sekcji omówiono podstawowe informacje dotyczące rozpoznawania odnoszące się do cyfrowego atramentu na platformie WPF.  
  
## <a name="recognition-solutions"></a>Rozwiązania rozpoznawania  
 Poniższy przykład pokazuje, jak rozpoznać atrament przy użyciu klasy [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  
  
> [!NOTE]
> Ten przykład wymaga zainstalowania rozpoznawania pisma ręcznego w systemie.  
  
 Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**. Zastąp zawartość pliku window1. XAML następującym kodem XAML. Ten kod renderuje interfejs użytkownika aplikacji.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Dodaj odwołanie do zestawu atramentu firmy Microsoft, Microsoft. Ink. dll, który można znaleźć w folderze \Program Files\Common Files\Microsoft Shared\Ink. Zastąp zawartość pliku związanego z kodem następującym kodem.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
