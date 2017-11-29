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
ms.openlocfilehash: 308b2152f98286ba532a15e5491b5d1a25aa66dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="ef8bf-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="ef8bf-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="ef8bf-103">Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że kodowania znaków specjalnych, takich jak znaki akcentu.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="ef8bf-104">Istnieje jednak zestaw często używane znaki specjalne, które są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="ef8bf-105">Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardowa do kodowania.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="ef8bf-106">W poniższej tabeli przedstawiono składnię kodowanie tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="ef8bf-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="ef8bf-107">Znak</span><span class="sxs-lookup"><span data-stu-id="ef8bf-107">Character</span></span>|<span data-ttu-id="ef8bf-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef8bf-108">Syntax</span></span>|<span data-ttu-id="ef8bf-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ef8bf-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="ef8bf-110">Mniej niż symbol.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="ef8bf-111">Większa niż znak.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="ef8bf-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="ef8bf-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="ef8bf-113">"</span><span class="sxs-lookup"><span data-stu-id="ef8bf-113">"</span></span>|`"`|<span data-ttu-id="ef8bf-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ef8bf-115">Jeśli utworzysz plik kodu znaczników przy użyciu tekstu edytor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, możesz zapisać plik [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania wszelkie znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="ef8bf-116">Poniższy przykład przedstawia sposób korzystania znaki specjalne w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="ef8bf-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef8bf-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef8bf-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
