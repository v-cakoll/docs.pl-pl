---
title: Jak użyć znaku specjalnego w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: c593ca094487e8f7016b02870026321fbcb9a7c3
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="9bc90-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="9bc90-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="9bc90-103">Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że kodowania znaków specjalnych, takich jak znaki akcentu.</span><span class="sxs-lookup"><span data-stu-id="9bc90-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="9bc90-104">Istnieje jednak zestaw często używane znaki specjalne, które są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="9bc90-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="9bc90-105">Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardowa do kodowania.</span><span class="sxs-lookup"><span data-stu-id="9bc90-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="9bc90-106">W poniższej tabeli przedstawiono składnię kodowanie tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="9bc90-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="9bc90-107">Znak</span><span class="sxs-lookup"><span data-stu-id="9bc90-107">Character</span></span>|<span data-ttu-id="9bc90-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bc90-108">Syntax</span></span>|<span data-ttu-id="9bc90-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9bc90-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="9bc90-110">Mniej niż symbol.</span><span class="sxs-lookup"><span data-stu-id="9bc90-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="9bc90-111">Większa niż znak.</span><span class="sxs-lookup"><span data-stu-id="9bc90-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="9bc90-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="9bc90-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="9bc90-113">"</span><span class="sxs-lookup"><span data-stu-id="9bc90-113">"</span></span>|`&quot;`|<span data-ttu-id="9bc90-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="9bc90-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9bc90-115">Jeśli utworzysz plik kodu znaczników przy użyciu tekstu edytor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, możesz zapisać plik [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania wszelkie znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="9bc90-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="9bc90-116">Poniższy przykład przedstawia sposób korzystania znaki specjalne w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="9bc90-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc90-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bc90-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
