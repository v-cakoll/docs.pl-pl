---
title: Jak zmienić FlowDirection zawartości za pomocą programowania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88beba371a9dd8ea54dabe8f541b4a01773982cb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a><span data-ttu-id="a33f0-102">Jak zmienić FlowDirection zawartości za pomocą programowania</span><span class="sxs-lookup"><span data-stu-id="a33f0-102">How to: Change the FlowDirection of Content Programmatically</span></span>
<span data-ttu-id="a33f0-103">W tym przykładzie pokazano, jak programowo zmienić <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.FlowDocumentReader>.</span><span class="sxs-lookup"><span data-stu-id="a33f0-103">This example shows how to programmatically change the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property of a <xref:System.Windows.Controls.FlowDocumentReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a33f0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a33f0-104">Example</span></span>  
 <span data-ttu-id="a33f0-105">Dwa <xref:System.Windows.Controls.Button> elementy są tworzone, każdy reprezentuje jedną z możliwych wartości <xref:System.Windows.FlowDirection>.</span><span class="sxs-lookup"><span data-stu-id="a33f0-105">Two <xref:System.Windows.Controls.Button> elements are created, each representing one of the possible values of <xref:System.Windows.FlowDirection>.</span></span> <span data-ttu-id="a33f0-106">Kliknięcie przycisku wartości właściwości skojarzonej, ponieważ jest stosowany do zawartości <xref:System.Windows.Controls.FlowDocumentReader> o nazwie `tf1`.</span><span class="sxs-lookup"><span data-stu-id="a33f0-106">When a button is clicked, the associated property value is applied to the contents of a <xref:System.Windows.Controls.FlowDocumentReader> named `tf1`.</span></span>  <span data-ttu-id="a33f0-107">Wartość właściwości są równocześnie zapisywane w <xref:System.Windows.Controls.TextBlock> o nazwie `txt1`.</span><span class="sxs-lookup"><span data-stu-id="a33f0-107">The property value is also written to a <xref:System.Windows.Controls.TextBlock> named `txt1`.</span></span>  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a><span data-ttu-id="a33f0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a33f0-108">Example</span></span>  
 <span data-ttu-id="a33f0-109">Zdarzenia powiązane z kliknięcia przycisków zdefiniowanych powyżej są obsługiwane w pliku związanym z kodem C#.</span><span class="sxs-lookup"><span data-stu-id="a33f0-109">The events associated with the button clicks defined above are handled in a C# code-behind file.</span></span>  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
