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
# <a name="handwriting-recognition"></a><span data-ttu-id="86b19-102">Rozpoznawanie pisma</span><span class="sxs-lookup"><span data-stu-id="86b19-102">Handwriting Recognition</span></span>
<span data-ttu-id="86b19-103">W tej sekcji omówiono podstawowe informacje na temat rozpoznawania w odniesieniu do cyfrowego pismo odręczne na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="86b19-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="86b19-104">Rozpoznawanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="86b19-104">Recognition Solutions</span></span>  
 <span data-ttu-id="86b19-105">Poniższy przykład przedstawia do rozpoznawania pisma odręcznego za pomocą [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="86b19-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86b19-106">W tym przykładzie wymaga zainstalowania aparaty rozpoznawania pisma ręcznego w systemie.</span><span class="sxs-lookup"><span data-stu-id="86b19-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="86b19-107">Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="86b19-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="86b19-108">Zastąp zawartość pliku Window1.xaml następujący kod XAML.</span><span class="sxs-lookup"><span data-stu-id="86b19-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="86b19-109">Ten kod renderuje interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86b19-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="86b19-110">Dodaj odwołanie do zestawu Microsoft Ink, Microsoft.Ink.dll, które znajdują się w \Program Files\Common Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="86b19-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="86b19-111">Zastąp zawartość pliku CodeBehind następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="86b19-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="86b19-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86b19-112">See Also</span></span>  
 <span data-ttu-id="86b19-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="86b19-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
