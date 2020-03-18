---
title: Ustawienia konfiguracji sieci
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują sieć dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802772"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="ff806-103">Opcje konfiguracji w czasie wykonywania sieci</span><span class="sxs-lookup"><span data-stu-id="ff806-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="ff806-104">Protokół HTTP/2</span><span class="sxs-lookup"><span data-stu-id="ff806-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="ff806-105">Określa, czy włączona jest obsługa protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="ff806-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="ff806-106">Domyślnie: Wyłączone`false`( ).</span><span class="sxs-lookup"><span data-stu-id="ff806-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="ff806-107">Wprowadzony w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ff806-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="ff806-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ff806-108">Setting name</span></span> | <span data-ttu-id="ff806-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="ff806-109">Values</span></span> |
| - | - |
| <span data-ttu-id="ff806-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ff806-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="ff806-111">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ff806-111">`false` - disabled</span></span><br/><span data-ttu-id="ff806-112">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="ff806-112">`true` - enabled</span></span> |
| <span data-ttu-id="ff806-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ff806-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="ff806-114">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ff806-114">`0` - disabled</span></span><br/><span data-ttu-id="ff806-115">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="ff806-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="ff806-116">Program obsługi HTTP gniazd</span><span class="sxs-lookup"><span data-stu-id="ff806-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="ff806-117">Konfiguruje, czy interfejsy API <xref:System.Net.Http.HttpClient>sieci <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> wysokiego poziomu, takie jak , użyj lub implementacja <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> tego jest oparta na [libcurl](https://curl.haxx.se/libcurl/).</span><span class="sxs-lookup"><span data-stu-id="ff806-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="ff806-118">Domyślnie: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Użyj ( ).</span><span class="sxs-lookup"><span data-stu-id="ff806-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="ff806-119">To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="ff806-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="ff806-120">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ff806-120">Setting name</span></span> | <span data-ttu-id="ff806-121">Wartości</span><span class="sxs-lookup"><span data-stu-id="ff806-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ff806-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ff806-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="ff806-123">`true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ff806-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ff806-124">`false`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ff806-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="ff806-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ff806-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="ff806-126">`1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ff806-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ff806-127">`0`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ff806-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
