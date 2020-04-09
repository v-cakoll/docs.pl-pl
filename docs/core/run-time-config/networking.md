---
title: Ustawienia konfiguracji sieciowej
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują sieć dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989106"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="739ea-103">Opcje konfiguracji w czasie wykonywania sieci</span><span class="sxs-lookup"><span data-stu-id="739ea-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="739ea-104">Protokół HTTP/2</span><span class="sxs-lookup"><span data-stu-id="739ea-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="739ea-105">Konfiguruje, czy obsługa protokołu HTTP/2 jest włączona.</span><span class="sxs-lookup"><span data-stu-id="739ea-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="739ea-106">Domyślnie:`false`Wyłączone ( ).</span><span class="sxs-lookup"><span data-stu-id="739ea-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="739ea-107">Wprowadzony w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="739ea-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="739ea-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="739ea-108">Setting name</span></span> | <span data-ttu-id="739ea-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="739ea-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="739ea-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="739ea-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="739ea-111">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="739ea-111">`false` - disabled</span></span><br/><span data-ttu-id="739ea-112">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="739ea-112">`true` - enabled</span></span> |
| <span data-ttu-id="739ea-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="739ea-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="739ea-114">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="739ea-114">`0` - disabled</span></span><br/><span data-ttu-id="739ea-115">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="739ea-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="739ea-116">UżyjsocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="739ea-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="739ea-117">Konfiguruje, <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> czy używa lub starszych stosów protokołu HTTP (<xref:System.Net.Http.WinHttpHandler> w systemie Windows i `CurlHandler`, klasa wewnętrzna zaimplementowana na szczycie [libcurl](https://curl.haxx.se/libcurl/), w systemie Linux).</span><span class="sxs-lookup"><span data-stu-id="739ea-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="739ea-118">Może być przy użyciu interfejsów API sieciowych wysokiego poziomu <xref:System.Net.Http.HttpClientHandler> zamiast bezpośredniego tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="739ea-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="739ea-119">To ustawienie ma również wpływ na to, który stos protokołu HTTP <xref:System.Net.Http.HttpClient> jest używany przez interfejsy API sieci wysokiego poziomu, w tym i [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span><span class="sxs-lookup"><span data-stu-id="739ea-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="739ea-120">Domyślnie: <xref:System.Net.Http.SocketsHttpHandler> `true`Użyj ( ).</span><span class="sxs-lookup"><span data-stu-id="739ea-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="739ea-121">To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="739ea-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="739ea-122">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="739ea-122">Setting name</span></span> | <span data-ttu-id="739ea-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="739ea-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="739ea-124">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="739ea-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="739ea-125">`true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="739ea-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="739ea-126">`false`- umożliwia korzystanie <xref:System.Net.Http.WinHttpHandler> z systemu Windows lub [libcurl](https://curl.haxx.se/libcurl/) na Linuksie</span><span class="sxs-lookup"><span data-stu-id="739ea-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="739ea-127">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="739ea-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="739ea-128">`1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="739ea-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="739ea-129">`0`- umożliwia korzystanie <xref:System.Net.Http.WinHttpHandler> z systemu Windows lub [libcurl](https://curl.haxx.se/libcurl/) na Linuksie</span><span class="sxs-lookup"><span data-stu-id="739ea-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="739ea-130">Począwszy od platformy .NET 5 `System.Net.Http.UseSocketsHttpHandler` ustawienie nie jest już dostępne.</span><span class="sxs-lookup"><span data-stu-id="739ea-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
