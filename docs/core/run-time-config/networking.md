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
# <a name="run-time-configuration-options-for-networking"></a>Opcje konfiguracji w czasie wykonywania sieci

## <a name="http2-protocol"></a>Protokół HTTP/2

- Konfiguruje, czy obsługa protokołu HTTP/2 jest włączona.
- Domyślnie:`false`Wyłączone ( ).
- Wprowadzony w .NET Core 3.0.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- niepełnosprawnych<br/>`true`- włączone |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- niepełnosprawnych<br/>`1`- włączone |

## <a name="usesocketshttphandler"></a>UżyjsocketsHttpHandler

- Konfiguruje, czy interfejsy API sieci <xref:System.Net.Http.HttpClient>wysokiego <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> poziomu, takie jak , użyj lub implementacji, że opiera się na [libcurl](https://curl.haxx.se/libcurl/).
- Domyślnie: <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> `true`Użyj ( ).
- To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler> |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umożliwia korzystanie z<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> Począwszy od platformy .NET 5 `System.Net.Http.UseSocketsHttpHandler` ustawienie nie jest już dostępne.
