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
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740842"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="ce139-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="ce139-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="ce139-103">Pliki znaczników, które są tworzone w programie Visual Studio, są automatycznie zapisywane w formacie Unicode UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="ce139-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="ce139-104">Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="ce139-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="ce139-105">Te znaki specjalne są zgodne ze standardem XML organizacja World Wide Web Consortium (W3C) do kodowania.</span><span class="sxs-lookup"><span data-stu-id="ce139-105">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="ce139-106">W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="ce139-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="ce139-107">Znak</span><span class="sxs-lookup"><span data-stu-id="ce139-107">Character</span></span>|<span data-ttu-id="ce139-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce139-108">Syntax</span></span>|<span data-ttu-id="ce139-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ce139-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="ce139-110">Mniejsze niż symbol.</span><span class="sxs-lookup"><span data-stu-id="ce139-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="ce139-111">Znak większości.</span><span class="sxs-lookup"><span data-stu-id="ce139-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="ce139-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="ce139-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="ce139-113">"</span><span class="sxs-lookup"><span data-stu-id="ce139-113">"</span></span>|`&quot;`|<span data-ttu-id="ce139-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="ce139-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ce139-115">Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w formacie Unicode UTF-8 pliku, aby zachować wszelkie kodowane znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="ce139-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="ce139-116">Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="ce139-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce139-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce139-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
