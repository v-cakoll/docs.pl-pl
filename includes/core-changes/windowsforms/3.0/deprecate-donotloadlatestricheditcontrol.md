---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937038"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="9ecf5-101">Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="9ecf5-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="9ecf5-102">Przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności, który został wprowadzony w programie .NET Framework 4.7.1, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9ecf5-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9ecf5-103">Change description</span></span>

<span data-ttu-id="9ecf5-104">W .NET Framework 4.6.2 i <xref:System.Windows.Forms.RichTextBox> poprzednich wersjach formant będzie utworzyć wystąpienia w usytuanym win32 RichEdit kontroli v3.0 i dla aplikacji, które są przeznaczone do .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> formant będzie wystąpienia RichEdit v4.1 (w *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="9ecf5-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="9ecf5-105">Przełącznik `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` zgodności został wprowadzony, aby umożliwić aplikacjom docelowym .NET Framework 4.7.1 i nowszym wersjom rezygnację z nowego formantu RichEdit v4.1 i zamiast tego użyj starego formantu RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="9ecf5-106">W .NET Core `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` przełącznik nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="9ecf5-107">Obsługiwane są tylko <xref:System.Windows.Forms.RichTextBox> nowe wersje formantu.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9ecf5-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9ecf5-108">Version introduced</span></span>

<span data-ttu-id="9ecf5-109">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="9ecf5-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9ecf5-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9ecf5-110">Recommended action</span></span>

<span data-ttu-id="9ecf5-111">Wyjmij przełącznik.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-111">Remove the switch.</span></span> <span data-ttu-id="9ecf5-112">Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="9ecf5-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="9ecf5-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9ecf5-113">Category</span></span>

<span data-ttu-id="9ecf5-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ecf5-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9ecf5-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9ecf5-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
