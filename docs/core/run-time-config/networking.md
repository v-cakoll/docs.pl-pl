---
title: Ustawienia konfiguracji sieci
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sieć dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802772"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="98bff-103">Opcje konfiguracji czasu wykonywania dla sieci</span><span class="sxs-lookup"><span data-stu-id="98bff-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="98bff-104">Protokół HTTP/2</span><span class="sxs-lookup"><span data-stu-id="98bff-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="98bff-105">Określa, czy jest włączona obsługa protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="98bff-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="98bff-106">Domyślnie: wyłączone (`false`).</span><span class="sxs-lookup"><span data-stu-id="98bff-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="98bff-107">Wprowadzone w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="98bff-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="98bff-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="98bff-108">Setting name</span></span> | <span data-ttu-id="98bff-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="98bff-109">Values</span></span> |
| - | - |
| <span data-ttu-id="98bff-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="98bff-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="98bff-111">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="98bff-111">`false` - disabled</span></span><br/><span data-ttu-id="98bff-112">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="98bff-112">`true` - enabled</span></span> |
| <span data-ttu-id="98bff-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="98bff-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="98bff-114">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="98bff-114">`0` - disabled</span></span><br/><span data-ttu-id="98bff-115">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="98bff-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="98bff-116">Obsługa protokołu HTTP Sockets</span><span class="sxs-lookup"><span data-stu-id="98bff-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="98bff-117">Określa, czy na wysokim poziomie interfejsów API sieci, takich jak <xref:System.Net.Http.HttpClient>, należy używać <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> lub implementacji <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> opartych na [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="98bff-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="98bff-118">Domyślne: Użyj <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span><span class="sxs-lookup"><span data-stu-id="98bff-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="98bff-119">To ustawienie można skonfigurować programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98bff-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="98bff-120">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="98bff-120">Setting name</span></span> | <span data-ttu-id="98bff-121">Wartości</span><span class="sxs-lookup"><span data-stu-id="98bff-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="98bff-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="98bff-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="98bff-123">`true` — umożliwia korzystanie z <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="98bff-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="98bff-124">`false` — umożliwia korzystanie z <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="98bff-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="98bff-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="98bff-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="98bff-126">`1` — umożliwia korzystanie z <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="98bff-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="98bff-127">`0` — umożliwia korzystanie z <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="98bff-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
