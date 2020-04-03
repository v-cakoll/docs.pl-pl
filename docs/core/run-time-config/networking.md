---
title: Ustawienia konfiguracji sieciowej
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują sieć dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635424"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="8aa6f-103">Opcje konfiguracji w czasie wykonywania sieci</span><span class="sxs-lookup"><span data-stu-id="8aa6f-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="8aa6f-104">Protokół HTTP/2</span><span class="sxs-lookup"><span data-stu-id="8aa6f-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="8aa6f-105">Konfiguruje, czy obsługa protokołu HTTP/2 jest włączona.</span><span class="sxs-lookup"><span data-stu-id="8aa6f-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="8aa6f-106">Domyślnie:`false`Wyłączone ( ).</span><span class="sxs-lookup"><span data-stu-id="8aa6f-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="8aa6f-107">Wprowadzony w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="8aa6f-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="8aa6f-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="8aa6f-108">Setting name</span></span> | <span data-ttu-id="8aa6f-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="8aa6f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="8aa6f-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8aa6f-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="8aa6f-111">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="8aa6f-111">`false` - disabled</span></span><br/><span data-ttu-id="8aa6f-112">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="8aa6f-112">`true` - enabled</span></span> |
| <span data-ttu-id="8aa6f-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="8aa6f-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="8aa6f-114">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="8aa6f-114">`0` - disabled</span></span><br/><span data-ttu-id="8aa6f-115">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="8aa6f-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="8aa6f-116">UżyjsocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="8aa6f-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="8aa6f-117">Konfiguruje, czy interfejsy API sieci <xref:System.Net.Http.HttpClient>wysokiego <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> poziomu, takie jak , użyj lub implementacji, że opiera się na [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="8aa6f-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="8aa6f-118">Domyślnie: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Użyj ( ).</span><span class="sxs-lookup"><span data-stu-id="8aa6f-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="8aa6f-119">To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="8aa6f-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="8aa6f-120">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="8aa6f-120">Setting name</span></span> | <span data-ttu-id="8aa6f-121">Wartości</span><span class="sxs-lookup"><span data-stu-id="8aa6f-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="8aa6f-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="8aa6f-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="8aa6f-123">`true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8aa6f-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8aa6f-124">`false`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="8aa6f-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="8aa6f-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="8aa6f-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="8aa6f-126">`1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8aa6f-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8aa6f-127">`0`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="8aa6f-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |

> [!NOTE]
> <span data-ttu-id="8aa6f-128">Począwszy od platformy .NET 5 `System.Net.Http.UseSocketsHttpHandler` ustawienie nie jest już dostępne.</span><span class="sxs-lookup"><span data-stu-id="8aa6f-128">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
