---
title: "Jak użyć znaku specjalnego w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79df87d716224cb8681c1688d94fe56077452c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="e3976-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="e3976-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="e3976-103">Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że kodowania znaków specjalnych, takich jak znaki akcentu.</span><span class="sxs-lookup"><span data-stu-id="e3976-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="e3976-104">Istnieje jednak zestaw często używane znaki specjalne, które są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="e3976-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="e3976-105">Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardowa do kodowania.</span><span class="sxs-lookup"><span data-stu-id="e3976-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="e3976-106">W poniższej tabeli przedstawiono składnię kodowanie tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="e3976-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="e3976-107">Znak</span><span class="sxs-lookup"><span data-stu-id="e3976-107">Character</span></span>|<span data-ttu-id="e3976-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3976-108">Syntax</span></span>|<span data-ttu-id="e3976-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e3976-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="e3976-110">Mniej niż symbol.</span><span class="sxs-lookup"><span data-stu-id="e3976-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="e3976-111">Większa niż znak.</span><span class="sxs-lookup"><span data-stu-id="e3976-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="e3976-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="e3976-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="e3976-113">"</span><span class="sxs-lookup"><span data-stu-id="e3976-113">"</span></span>|`"`|<span data-ttu-id="e3976-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="e3976-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e3976-115">Jeśli utworzysz plik kodu znaczników przy użyciu tekstu edytor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, możesz zapisać plik [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania wszelkie znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="e3976-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="e3976-116">Poniższy przykład przedstawia sposób korzystania znaki specjalne w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="e3976-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3976-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3976-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
