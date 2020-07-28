---
title: Jak użyć znaku specjalnego w XAML
description: Dowiedz się więcej o składni kodowania znaków specjalnych w formacie pliku Unicode UTF-8 w programie Visual Studio do użycia w plikach XAML w Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168356"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="b2456-103">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="b2456-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="b2456-104">Pliki znaczników, które są tworzone w programie Visual Studio, są automatycznie zapisywane w formacie Unicode UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="b2456-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="b2456-105">Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="b2456-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="b2456-106">Te znaki specjalne są zgodne ze standardem XML organizacja World Wide Web Consortium (W3C) do kodowania.</span><span class="sxs-lookup"><span data-stu-id="b2456-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="b2456-107">W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="b2456-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="b2456-108">Znak</span><span class="sxs-lookup"><span data-stu-id="b2456-108">Character</span></span>|<span data-ttu-id="b2456-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2456-109">Syntax</span></span>|<span data-ttu-id="b2456-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b2456-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="b2456-111">Mniejsze niż symbol.</span><span class="sxs-lookup"><span data-stu-id="b2456-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="b2456-112">Znak większości.</span><span class="sxs-lookup"><span data-stu-id="b2456-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="b2456-113">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="b2456-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="b2456-114">"</span><span class="sxs-lookup"><span data-stu-id="b2456-114">"</span></span>|`&quot;`|<span data-ttu-id="b2456-115">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="b2456-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b2456-116">Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w formacie Unicode UTF-8 pliku, aby zachować wszelkie kodowane znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="b2456-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="b2456-117">Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="b2456-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2456-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2456-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
