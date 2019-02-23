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
ms.openlocfilehash: a93c1486f191df31213fc6c85254ecd8801799b8
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747304"
---
# <a name="handwriting-recognition"></a>Rozpoznawanie pisma
W tej sekcji omówiono podstawy rozpoznawania w odniesieniu do cyfrowy atrament na platformie WPF.  
  
## <a name="recognition-solutions"></a>Rozpoznawanie rozwiązania  
 Poniższy przykład pokazuje, jak rozpoznawanie pisma odręcznego za pomocą [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) klasy.  
  
> [!NOTE]
>  Ten przykładowy skrypt wymaga zainstalowania aparaty rozpoznawania pisma ręcznego w systemie.  
  
 Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**. Zastąp zawartość pliku Window1.xaml poniższy kod XAML. Ten kod renderuje interfejsu użytkownika aplikacji.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Dodaj odwołanie do zestawu Microsoft Ink Microsoft.Ink.dll, który można znaleźć w \Program Files\Common Files\Microsoft Shared\Ink. Zastąp zawartość pliku CodeBehind następującym kodem.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
