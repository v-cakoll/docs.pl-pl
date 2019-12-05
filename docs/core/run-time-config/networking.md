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
# <a name="run-time-configuration-options-for-networking"></a>Opcje konfiguracji czasu wykonywania dla sieci

## <a name="http2-protocol"></a>Protokół HTTP/2

- Określa, czy jest włączona obsługa protokołu HTTP/2.
- Domyślnie: wyłączone (`false`).
- Wprowadzone w programie .NET Core 3,0.

| | Nazwa ustawienia | Wartości |
| - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` — wyłączone<br/>`true` — włączono |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` — wyłączone<br/>`1` — włączono |

## <a name="sockets-http-handler"></a>Obsługa protokołu HTTP Sockets

- Określa, czy na wysokim poziomie interfejsów API sieci, takich jak <xref:System.Net.Http.HttpClient>, należy używać <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> lub implementacji <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> opartych na [libcurl](https://curl.haxx.se/libcurl/).
- Domyślne: Użyj <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).
- To ustawienie można skonfigurować programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true` — umożliwia korzystanie z <xref:System.Net.Http.SocketsHttpHandler><br/>`false` — umożliwia korzystanie z <xref:System.Net.Http.HttpClientHandler> |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` — umożliwia korzystanie z <xref:System.Net.Http.SocketsHttpHandler><br/>`0` — umożliwia korzystanie z <xref:System.Net.Http.HttpClientHandler> |
