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
# <a name="run-time-configuration-options-for-networking"></a>Opcje konfiguracji w czasie wykonywania sieci

## <a name="http2-protocol"></a>Protokół HTTP/2

- Określa, czy włączona jest obsługa protokołu HTTP/2.
- Domyślnie: Wyłączone`false`( ).
- Wprowadzony w .NET Core 3.0.

| | Nazwa ustawienia | Wartości |
| - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- wyłączone<br/>`true`- włączona |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- wyłączone<br/>`1`- włączona |

## <a name="sockets-http-handler"></a>Program obsługi HTTP gniazd

- Konfiguruje, czy interfejsy API <xref:System.Net.Http.HttpClient>sieci <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> wysokiego poziomu, takie jak , użyj lub implementacja <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> tego jest oparta na [libcurl](https://curl.haxx.se/libcurl/).
- Domyślnie: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Użyj ( ).
- To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler> |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler> |
