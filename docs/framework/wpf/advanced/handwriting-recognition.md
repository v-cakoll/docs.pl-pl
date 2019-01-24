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
ms.openlocfilehash: 8f520b80970bfeebdfea01a6c722634efd99ffe7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725392"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="2811e-102">Rozpoznawanie pisma</span><span class="sxs-lookup"><span data-stu-id="2811e-102">Handwriting Recognition</span></span>
<span data-ttu-id="2811e-103">W tej sekcji omówiono podstawy rozpoznawania w odniesieniu do cyfrowy atrament na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="2811e-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="2811e-104">Rozpoznawanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="2811e-104">Recognition Solutions</span></span>  
 <span data-ttu-id="2811e-105">Poniższy przykład pokazuje, jak rozpoznawanie pisma odręcznego za pomocą [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) klasy.</span><span class="sxs-lookup"><span data-stu-id="2811e-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2811e-106">Ten przykładowy skrypt wymaga zainstalowania aparaty rozpoznawania pisma ręcznego w systemie.</span><span class="sxs-lookup"><span data-stu-id="2811e-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="2811e-107">Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="2811e-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="2811e-108">Zastąp zawartość pliku Window1.xaml poniższy kod XAML.</span><span class="sxs-lookup"><span data-stu-id="2811e-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="2811e-109">Ten kod renderuje interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2811e-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="2811e-110">Dodaj odwołanie do zestawu Microsoft Ink Microsoft.Ink.dll, który można znaleźć w \Program Files\Common Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="2811e-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="2811e-111">Zastąp zawartość pliku CodeBehind następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="2811e-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2811e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2811e-112">See also</span></span>
- <span data-ttu-id="2811e-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2811e-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
