---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620417"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="597dd-101">PreviewLostKeyboardFocus jest wywoływana wielokrotnie, jeśli jej program obsługi wyświetli okno komunikatu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="597dd-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="597dd-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="597dd-102">Details</span></span>

<span data-ttu-id="597dd-103">Począwszy od .NET Framework 4,5, wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> programu obsługi spowoduje ponowne uruchomienie programu obsługi po zamknięciu okna komunikatu, co może spowodować powstanie nieskończonej pętli okien komunikatów.</span><span class="sxs-lookup"><span data-stu-id="597dd-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="597dd-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="597dd-104">Suggestion</span></span>

<span data-ttu-id="597dd-105">Istnieją dwie opcje obejścia tego problemu:</span><span class="sxs-lookup"><span data-stu-id="597dd-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="597dd-106">Można to uniknąć, wywołując <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="597dd-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="597dd-107">Można to uniknąć, wyświetlając okno komunikatu z <xref:System.Windows.UIElement.LostKeyboardFocus> programu obsługi zdarzeń (w przeciwieństwie do <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> programu obsługi zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="597dd-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="597dd-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="597dd-108">Name</span></span>    | <span data-ttu-id="597dd-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="597dd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="597dd-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="597dd-110">Scope</span></span>   |<span data-ttu-id="597dd-111">Brzeg</span><span class="sxs-lookup"><span data-stu-id="597dd-111">Edge</span></span>|
|<span data-ttu-id="597dd-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="597dd-112">Version</span></span>|<span data-ttu-id="597dd-113">4.5</span><span class="sxs-lookup"><span data-stu-id="597dd-113">4.5</span></span>|
|<span data-ttu-id="597dd-114">Typ</span><span class="sxs-lookup"><span data-stu-id="597dd-114">Type</span></span>|<span data-ttu-id="597dd-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="597dd-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="597dd-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="597dd-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
