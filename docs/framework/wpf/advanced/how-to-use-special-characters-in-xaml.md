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
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918437"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="4b38f-102">Instrukcje: Używanie znaku specjalnego w XAML</span><span class="sxs-lookup"><span data-stu-id="4b38f-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="4b38f-103">Pliki znaczników, które są tworzone [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] w programie, są automatycznie [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] zapisywane w formacie pliku UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="4b38f-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="4b38f-104">Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="4b38f-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="4b38f-105">Te znaki specjalne są zgodne [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] ze [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardem kodowania.</span><span class="sxs-lookup"><span data-stu-id="4b38f-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="4b38f-106">W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:</span><span class="sxs-lookup"><span data-stu-id="4b38f-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="4b38f-107">Znak</span><span class="sxs-lookup"><span data-stu-id="4b38f-107">Character</span></span>|<span data-ttu-id="4b38f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b38f-108">Syntax</span></span>|<span data-ttu-id="4b38f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4b38f-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="4b38f-110">Mniejsze niż symbol.</span><span class="sxs-lookup"><span data-stu-id="4b38f-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="4b38f-111">Znak większości.</span><span class="sxs-lookup"><span data-stu-id="4b38f-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="4b38f-112">Symbol handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="4b38f-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="4b38f-113">"</span><span class="sxs-lookup"><span data-stu-id="4b38f-113">"</span></span>|`&quot;`|<span data-ttu-id="4b38f-114">Symbol podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="4b38f-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4b38f-115">Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formacie UTF-8, aby zachować wszelkie zakodowane znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="4b38f-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="4b38f-116">Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="4b38f-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b38f-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b38f-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
