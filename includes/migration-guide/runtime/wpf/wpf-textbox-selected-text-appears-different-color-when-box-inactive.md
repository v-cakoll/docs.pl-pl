---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235758"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="2d01a-101">TextBox WPF zaznaczony tekst jest wyświetlany inny kolor, gdy pole tekstowe jest nieaktywny</span><span class="sxs-lookup"><span data-stu-id="2d01a-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2d01a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2d01a-102">Details</span></span>|<span data-ttu-id="2d01a-103">W .NET Framework 4.5, gdy formant pola tekstowego WPF jest nieaktywny (nie ma fokusu), zaznaczony tekst wewnątrz pola będą wyświetlane w innym kolorze niż gdy kontrolka jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="2d01a-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="2d01a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="2d01a-104">Suggestion</span></span>|<span data-ttu-id="2d01a-105">Poprzednie zachowanie (.NET Framework 4.0) mogą zostać przywrócone, ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwość <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="2d01a-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="2d01a-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="2d01a-106">Scope</span></span>|<span data-ttu-id="2d01a-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="2d01a-107">Edge</span></span>|
|<span data-ttu-id="2d01a-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="2d01a-108">Version</span></span>|<span data-ttu-id="2d01a-109">4.5</span><span class="sxs-lookup"><span data-stu-id="2d01a-109">4.5</span></span>|
|<span data-ttu-id="2d01a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="2d01a-110">Type</span></span>|<span data-ttu-id="2d01a-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2d01a-111">Runtime</span></span>|
|<span data-ttu-id="2d01a-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2d01a-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
