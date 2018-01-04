---
title: Rozpoznawanie pisma
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
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 384f21587c29e6afe82964fc28432f5a6be92b05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="handwriting-recognition"></a>Rozpoznawanie pisma
W tej sekcji omówiono podstawowe informacje na temat rozpoznawania w odniesieniu do cyfrowego pismo odręczne na platformie WPF.  
  
## <a name="recognition-solutions"></a>Rozpoznawanie rozwiązania  
 Poniższy przykład przedstawia do rozpoznawania pisma odręcznego za pomocą [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) klasy.  
  
> [!NOTE]
>  W tym przykładzie wymaga zainstalowania aparaty rozpoznawania pisma ręcznego w systemie.  
  
 Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**. Zastąp zawartość pliku Window1.xaml następujący kod XAML. Ten kod renderuje interfejsu użytkownika aplikacji.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Dodaj odwołanie do zestawu Microsoft Ink, Microsoft.Ink.dll, które znajdują się w \Program Files\Common Files\Microsoft Shared\Ink. Zastąp zawartość pliku CodeBehind następującym kodem.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
