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
# <a name="handwriting-recognition"></a><span data-ttu-id="168d7-102">Rozpoznawanie pisma</span><span class="sxs-lookup"><span data-stu-id="168d7-102">Handwriting Recognition</span></span>
<span data-ttu-id="168d7-103">W tej sekcji omówiono podstawowe informacje dotyczące rozpoznawania odnoszące się do cyfrowego atramentu na platformie WPF.</span><span class="sxs-lookup"><span data-stu-id="168d7-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="168d7-104">Rozwiązania rozpoznawania</span><span class="sxs-lookup"><span data-stu-id="168d7-104">Recognition Solutions</span></span>  
 <span data-ttu-id="168d7-105">Poniższy przykład pokazuje, jak rozpoznać atrament przy użyciu klasy [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .</span><span class="sxs-lookup"><span data-stu-id="168d7-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="168d7-106">Ten przykład wymaga zainstalowania rozpoznawania pisma ręcznego w systemie.</span><span class="sxs-lookup"><span data-stu-id="168d7-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="168d7-107">Utwórz nowy projekt aplikacji WPF w programie Visual Studio o nazwie **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="168d7-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="168d7-108">Zastąp zawartość pliku window1. XAML następującym kodem XAML.</span><span class="sxs-lookup"><span data-stu-id="168d7-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="168d7-109">Ten kod renderuje interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="168d7-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="168d7-110">Dodaj odwołanie do zestawu atramentu firmy Microsoft, Microsoft. Ink. dll, który można znaleźć w folderze \Program Files\Common Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="168d7-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="168d7-111">Zastąp zawartość pliku związanego z kodem następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="168d7-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="168d7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="168d7-112">See also</span></span>

- <span data-ttu-id="168d7-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="168d7-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
