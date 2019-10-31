---
title: 'Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5174c67e4204c2e20e5730ab7c092ccbb0aeda1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126264"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="24150-102">Łagodzenie: niestandardowe implementacje IMessageFilter. PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="24150-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="24150-103">W Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework zaczynających się od .NET Framework 4.6.1, niestandardowa implementacja <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować komunikaty, gdy metoda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> jest wywoływana, jeśli <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacja:</span><span class="sxs-lookup"><span data-stu-id="24150-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="24150-104">Wykonuje jedną lub obie następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="24150-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="24150-105">Dodaje filtr komunikatów przez wywołanie metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="24150-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="24150-106">Usuwa filtr komunikatów przez wywołanie metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="24150-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="24150-107">Method.</span><span class="sxs-lookup"><span data-stu-id="24150-107">method.</span></span>

- <span data-ttu-id="24150-108">**I** pompy komunikatów przez wywołanie metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24150-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="24150-109">Wpływ</span><span class="sxs-lookup"><span data-stu-id="24150-109">Impact</span></span>

<span data-ttu-id="24150-110">Ta zmiana ma wpływ tylko na Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework, począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="24150-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="24150-111">W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji .NET Framework takie implementacje w niektórych przypadkach zgłaszają wyjątek <xref:System.IndexOutOfRangeException>, gdy wywoływana jest metoda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="24150-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="24150-112">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="24150-112">Mitigation</span></span>

<span data-ttu-id="24150-113">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji\<do sekcji [> środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="24150-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="24150-114">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 lub nowszej wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do sekcji [> runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="24150-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="24150-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24150-115">See also</span></span>

- [<span data-ttu-id="24150-116">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="24150-116">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
