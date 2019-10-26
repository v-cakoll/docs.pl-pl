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
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919643"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="b0aa9-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="b0aa9-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="b0aa9-103">Pliki znaczników, które są tworzone w programie Visual Studio, są automatycznie zapisywane w formacie Unicode UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="b0aa9-104">Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="b0aa9-105">Te znaki specjalne są zgodne ze standardem [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] organizacja World Wide Web Consortium (W3C) do kodowania.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-105">These special characters follow the World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="b0aa9-106">W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="b0aa9-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="b0aa9-107">Znak</span><span class="sxs-lookup"><span data-stu-id="b0aa9-107">Character</span></span>|<span data-ttu-id="b0aa9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0aa9-108">Syntax</span></span>|<span data-ttu-id="b0aa9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b0aa9-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="b0aa9-110">Mniejsze niż symbol.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="b0aa9-111">Znak większości.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="b0aa9-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="b0aa9-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="b0aa9-113">"</span><span class="sxs-lookup"><span data-stu-id="b0aa9-113">"</span></span>|`&quot;`|<span data-ttu-id="b0aa9-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b0aa9-115">Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w formacie Unicode UTF-8 pliku, aby zachować wszelkie kodowane znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="b0aa9-116">Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="b0aa9-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0aa9-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0aa9-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
