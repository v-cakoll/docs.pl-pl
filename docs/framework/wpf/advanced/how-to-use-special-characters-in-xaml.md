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
ms.openlocfilehash: 27f2b18593d075b54eb8c3351bbb84415700cfd4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395803"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="31ba2-102">Jak użyć znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="31ba2-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="31ba2-103">Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w formacie Unicode UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="31ba2-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="31ba2-104">Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="31ba2-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="31ba2-105">Te znaki specjalne są zgodne ze standardem dla kodowania [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31ba2-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="31ba2-106">W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="31ba2-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="31ba2-107">Znak</span><span class="sxs-lookup"><span data-stu-id="31ba2-107">Character</span></span>|<span data-ttu-id="31ba2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="31ba2-108">Syntax</span></span>|<span data-ttu-id="31ba2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="31ba2-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="31ba2-110">Mniejsze niż symbol.</span><span class="sxs-lookup"><span data-stu-id="31ba2-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="31ba2-111">Znak większości.</span><span class="sxs-lookup"><span data-stu-id="31ba2-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="31ba2-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="31ba2-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="31ba2-113">"</span><span class="sxs-lookup"><span data-stu-id="31ba2-113">"</span></span>|`&quot;`|<span data-ttu-id="31ba2-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="31ba2-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="31ba2-115">Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w formacie Unicode UTF-8 pliku, aby zachować wszelkie kodowane znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="31ba2-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="31ba2-116">Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="31ba2-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31ba2-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="31ba2-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
