---
title: Środki zaradcze Niestandardowe implementacje IMessageFilter. PreFilterMessage
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779432"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="a0f1a-102">Środki zaradcze Niestandardowe implementacje IMessageFilter. PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="a0f1a-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="a0f1a-103">W Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework począwszy od .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować komunikaty, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> Metoda jest wywoływana, jeśli implementacja:</span><span class="sxs-lookup"><span data-stu-id="a0f1a-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="a0f1a-104">Wykonuje jedną lub obie następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="a0f1a-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="a0f1a-105">Dodaje filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a0f1a-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="a0f1a-106">Usuwa filtr komunikatów przez wywołanie <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a0f1a-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="a0f1a-107">Method.</span><span class="sxs-lookup"><span data-stu-id="a0f1a-107">method.</span></span>

- <span data-ttu-id="a0f1a-108">**I** pompy komunikatów przez wywołanie <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a0f1a-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="a0f1a-109">Wpływ</span><span class="sxs-lookup"><span data-stu-id="a0f1a-109">Impact</span></span>

<span data-ttu-id="a0f1a-110">Ta zmiana ma wpływ tylko na Windows Forms aplikacje, które są przeznaczone dla wersji .NET Framework, począwszy od .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="a0f1a-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="a0f1a-111">W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji .NET Framework takie implementacje w niektórych przypadkach <xref:System.IndexOutOfRangeException> zgłaszają wyjątek, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> gdy wywoływana jest metoda</span><span class="sxs-lookup"><span data-stu-id="a0f1a-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="a0f1a-112">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="a0f1a-112">Mitigation</span></span>

<span data-ttu-id="a0f1a-113">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niego, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracyjnym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a0f1a-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="a0f1a-114">Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 lub nowszej wersji, mogą zrezygnować z tego zachowania, dodając następujące ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) plik konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="a0f1a-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="a0f1a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0f1a-115">See also</span></span>

- [<span data-ttu-id="a0f1a-116">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="a0f1a-116">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
