---
title: 'Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4faf42d3be4f76e5908068b1c2f88d7803ae18df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979345"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="49931-102">Środki zaradcze: Implementacji niestandardowego IMessageFilter.PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="49931-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="49931-103">W aplikacjach Windows Forms, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], niestandardowe <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji może bezpiecznie filtr komunikatów, kiedy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, gdy <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacji:</span><span class="sxs-lookup"><span data-stu-id="49931-103">In Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="49931-104">Wykonuje jedno lub oba z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="49931-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="49931-105">Dodaje filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49931-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="49931-106">Usuwa filtr komunikatu przez wywołanie metody <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="49931-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="49931-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="49931-107">method.</span></span>

- <span data-ttu-id="49931-108">**I** pompy komunikatów przez wywołanie metody <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="49931-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="49931-109">Wpływ</span><span class="sxs-lookup"><span data-stu-id="49931-109">Impact</span></span>

<span data-ttu-id="49931-110">Ta zmiana dotyczy tylko aplikacji Windows Forms, przeznaczonych dla wersji programu .NET Framework począwszy od [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49931-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>

<span data-ttu-id="49931-111">W przypadku aplikacji Windows Forms przeznaczone dla poprzednich wersji programu .NET Framework, throw takich implementacji w niektórych przypadkach <xref:System.IndexOutOfRangeException> wyjątek podczas <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> wywoływana jest metoda</span><span class="sxs-lookup"><span data-stu-id="49931-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="49931-112">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="49931-112">Mitigation</span></span>

<span data-ttu-id="49931-113">Jeśli ta zmiana jest niepożądany, aplikacje przeznaczone na platformę [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji można zrezygnować z go, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="49931-113">If this change is undesirable, apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="49931-114">Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub nowszej wersji można jednak to zachowanie, dodając następujące ustawienie konfiguracji, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)sekcję pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="49931-114">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="49931-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49931-115">See also</span></span>

- [<span data-ttu-id="49931-116">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="49931-116">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
