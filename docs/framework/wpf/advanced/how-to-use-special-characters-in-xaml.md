---
title: 'Instrukcje: Używanie znaku specjalnego w XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051086"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="858c1-102">Instrukcje: Używanie znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="858c1-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="858c1-103">Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że znaków specjalnych, takich jak znaki akcentu są kodowane niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="858c1-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="858c1-104">Jednak to zbiór często używane znaki specjalne, które są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="858c1-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="858c1-105">Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard kodowania.</span><span class="sxs-lookup"><span data-stu-id="858c1-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="858c1-106">W poniższej tabeli przedstawiono składnię tego zestawu znaków specjalnych kodowania:</span><span class="sxs-lookup"><span data-stu-id="858c1-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="858c1-107">Znak</span><span class="sxs-lookup"><span data-stu-id="858c1-107">Character</span></span>|<span data-ttu-id="858c1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="858c1-108">Syntax</span></span>|<span data-ttu-id="858c1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="858c1-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="858c1-110">Mniej niż symbol.</span><span class="sxs-lookup"><span data-stu-id="858c1-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="858c1-111">Większa niż logowania.</span><span class="sxs-lookup"><span data-stu-id="858c1-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="858c1-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="858c1-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="858c1-113">"</span><span class="sxs-lookup"><span data-stu-id="858c1-113">"</span></span>|`&quot;`|<span data-ttu-id="858c1-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="858c1-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="858c1-115">Jeśli tworzysz pliku znaczników przy użyciu typu text editor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, musisz zapisać plik w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania dowolne znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="858c1-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="858c1-116">Poniższy przykład pokazuje, jak możesz mogą używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="858c1-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="858c1-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="858c1-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
