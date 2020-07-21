---
title: 'Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage'
description: Dowiedz się więcej o niestandardowej IMessageFilter. PreFilterMessage implementacji zawartej w aplikacjach Windows Forms przeznaczonych dla .NET Framework 4.6.1 i nowszych.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475258"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="713b3-103">Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="713b3-103">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="713b3-104">W Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować komunikaty, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> Metoda jest wywoływana, jeśli <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacja:</span><span class="sxs-lookup"><span data-stu-id="713b3-104">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="713b3-105">Wykonuje jedną lub obie następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="713b3-105">Does one or both of the following:</span></span>

  - <span data-ttu-id="713b3-106">Dodaje filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="713b3-106">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="713b3-107">Usuwa filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="713b3-107">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="713b3-108">Method.</span><span class="sxs-lookup"><span data-stu-id="713b3-108">method.</span></span>

- <span data-ttu-id="713b3-109">**I** pompy komunikatów przez wywołanie <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="713b3-109">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="713b3-110">Wpływ</span><span class="sxs-lookup"><span data-stu-id="713b3-110">Impact</span></span>

<span data-ttu-id="713b3-111">Ta zmiana ma wpływ tylko na Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework, począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="713b3-111">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="713b3-112">W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji .NET Framework takie implementacje w niektórych przypadkach zgłaszają <xref:System.IndexOutOfRangeException> wyjątek, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wywoływana jest metoda</span><span class="sxs-lookup"><span data-stu-id="713b3-112">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="713b3-113">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="713b3-113">Mitigation</span></span>

<span data-ttu-id="713b3-114">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="713b3-114">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="713b3-115">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 lub nowszej wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="713b3-115">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="713b3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="713b3-116">See also</span></span>

- [<span data-ttu-id="713b3-117">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="713b3-117">Application compatibility</span></span>](application-compatibility.md)
