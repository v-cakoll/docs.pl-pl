---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614880"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="c4684-101">Właściwość ContextMenuStrip. SourceControl zawiera prawidłową kontrolkę w przypadku zagnieżdżonych kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c4684-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="c4684-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c4684-102">Details</span></span>

<span data-ttu-id="c4684-103">W .NET Framework 4.7.1 i poprzednich wersjach <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> Właściwość nieprawidłowo zwraca wartość null, jeśli użytkownik otworzy menu z formantów zagnieżdżonych <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="c4684-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="c4684-104">W .NET Framework 4.7.2 i nowszych <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> Właściwość jest zawsze ustawiana na rzeczywistą kontrolę źródła.</span><span class="sxs-lookup"><span data-stu-id="c4684-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c4684-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c4684-105">Suggestion</span></span>

<span data-ttu-id="c4684-106">**Jak wybrać lub wycofać te zmiany** Aby aplikacja mogła korzystać z tych zmian, musi ona działać na .NET Framework 4.7.2 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="c4684-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="c4684-107">Aplikacja może korzystać z tych zmian w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="c4684-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="c4684-108">Jest ona przeznaczona dla .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="c4684-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="c4684-109">Ta zmiana jest domyślnie włączona w Windows Forms aplikacjach przeznaczonych dla .NET Framework 4.7.2 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="c4684-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="c4684-110">Jest ona przeznaczona dla .NET Framework 4.7.1 lub wcześniejszej wersji i [wyłączają](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) się ze starszych zachowań ułatwień dostępu, dodając następujący `<runtime>` przykład AppContext do sekcji pliku app.config i ustawiając go na `false` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4684-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="c4684-111">Aplikacje ukierunkowane na .NET Framework 4.7.2 lub nowsze i chcą zachować starsze zachowanie mogą zrezygnować z używania wartości kontroli źródła starszej przez jawne ustawienie tego przełącznika AppContext na `true` .</span><span class="sxs-lookup"><span data-stu-id="c4684-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="c4684-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c4684-112">Name</span></span>    | <span data-ttu-id="c4684-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="c4684-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c4684-114">Zakres</span><span class="sxs-lookup"><span data-stu-id="c4684-114">Scope</span></span>   | <span data-ttu-id="c4684-115">Brzeg</span><span class="sxs-lookup"><span data-stu-id="c4684-115">Edge</span></span>        |
| <span data-ttu-id="c4684-116">Wersja</span><span class="sxs-lookup"><span data-stu-id="c4684-116">Version</span></span> | <span data-ttu-id="c4684-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c4684-117">4.7.2</span></span>       |
| <span data-ttu-id="c4684-118">Typ</span><span class="sxs-lookup"><span data-stu-id="c4684-118">Type</span></span>    | <span data-ttu-id="c4684-119">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="c4684-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c4684-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c4684-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
