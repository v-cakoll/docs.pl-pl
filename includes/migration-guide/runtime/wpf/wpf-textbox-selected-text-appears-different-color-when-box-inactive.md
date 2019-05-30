---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379688"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="d9e94-101">TextBox WPF zaznaczony tekst jest wyświetlany inny kolor, gdy pole tekstowe jest nieaktywny</span><span class="sxs-lookup"><span data-stu-id="d9e94-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d9e94-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d9e94-102">Details</span></span>|<span data-ttu-id="d9e94-103">W .NET Framework 4.5, gdy formant pola tekstowego WPF jest nieaktywny (nie ma fokusu), zaznaczony tekst wewnątrz pola będą wyświetlane w innym kolorze niż gdy kontrolka jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="d9e94-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="d9e94-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d9e94-104">Suggestion</span></span>|<span data-ttu-id="d9e94-105">Poprzednie zachowanie (.NET Framework 4.0) mogą zostać przywrócone, ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwość <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="d9e94-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="d9e94-106">Scope</span><span class="sxs-lookup"><span data-stu-id="d9e94-106">Scope</span></span>|<span data-ttu-id="d9e94-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="d9e94-107">Edge</span></span>|
|<span data-ttu-id="d9e94-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="d9e94-108">Version</span></span>|<span data-ttu-id="d9e94-109">4.5</span><span class="sxs-lookup"><span data-stu-id="d9e94-109">4.5</span></span>|
|<span data-ttu-id="d9e94-110">Typ</span><span class="sxs-lookup"><span data-stu-id="d9e94-110">Type</span></span>|<span data-ttu-id="d9e94-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d9e94-111">Runtime</span></span>|
|<span data-ttu-id="d9e94-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d9e94-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
