---
title: 'Łagodzenie: Niestandardowe implementacje IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400121"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="318e4-102">Łagodzenie: Niestandardowe implementacje IMessageFilter.PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="318e4-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="318e4-103">W aplikacjach Windows Forms, które są przeznaczone dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1, implementacja niestandardowa <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> może bezpiecznie filtrować wiadomości, gdy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda jest wywoływana, jeśli <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementacja:</span><span class="sxs-lookup"><span data-stu-id="318e4-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="318e4-104">Czy jedna lub obie z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="318e4-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="318e4-105">Dodaje filtr wiadomości, <xref:System.Windows.Forms.Application.AddMessageFilter%2A> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="318e4-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="318e4-106">Usuwa filtr wiadomości, wywołując <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="318e4-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="318e4-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="318e4-107">method.</span></span>

- <span data-ttu-id="318e4-108">**I** pompuje wiadomości, <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="318e4-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="318e4-109">Wpływ</span><span class="sxs-lookup"><span data-stu-id="318e4-109">Impact</span></span>

<span data-ttu-id="318e4-110">Ta zmiana dotyczy tylko aplikacji Windows Forms, które są przeznaczone dla wersji programu .NET Framework, począwszy od programu .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="318e4-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="318e4-111">W przypadku aplikacji Windows Forms przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> takie implementacje w niektórych przypadkach zgłaszają wyjątek, <xref:System.IndexOutOfRangeException> gdy metoda jest wywoływana</span><span class="sxs-lookup"><span data-stu-id="318e4-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="318e4-112">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="318e4-112">Mitigation</span></span>

<span data-ttu-id="318e4-113">Jeśli ta zmiana jest niepożądana, aplikacje przeznaczone dla programu .NET Framework 4.6.1 lub nowszej wersji mogą zrezygnować z niej, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="318e4-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="318e4-114">Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale uruchomione w ramach programu .NET Framework 4.6.1 lub nowszej wersji, mogą zdecydować się na to zachowanie, dodając następujące ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracyjnego aplikacji:</span><span class="sxs-lookup"><span data-stu-id="318e4-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="318e4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="318e4-115">See also</span></span>

- [<span data-ttu-id="318e4-116">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="318e4-116">Application compatibility</span></span>](application-compatibility.md)
