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

- Konfiguruje, <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> czy używa lub starszych stosów protokołu HTTP (<xref:System.Net.Http.WinHttpHandler> w systemie Windows i `CurlHandler`, klasa wewnętrzna zaimplementowana na szczycie [libcurl](https://curl.haxx.se/libcurl/), w systemie Linux).

  > [!NOTE]
  > Może być przy użyciu interfejsów API sieciowych wysokiego poziomu <xref:System.Net.Http.HttpClientHandler> zamiast bezpośredniego tworzenia wystąpienia klasy. To ustawienie ma również wpływ na to, który stos protokołu HTTP <xref:System.Net.Http.HttpClient> jest używany przez interfejsy API sieci wysokiego poziomu, w tym i [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Domyślnie: <xref:System.Net.Http.SocketsHttpHandler> `true`Użyj ( ).

- To ustawienie można skonfigurować programowo, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> wywołując metodę.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- umożliwia korzystanie <xref:System.Net.Http.WinHttpHandler> z systemu Windows lub [libcurl](https://curl.haxx.se/libcurl/) na Linuksie |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- umożliwia korzystanie <xref:System.Net.Http.WinHttpHandler> z systemu Windows lub [libcurl](https://curl.haxx.se/libcurl/) na Linuksie |

> [!NOTE]
> Począwszy od platformy .NET 5 `System.Net.Http.UseSocketsHttpHandler` ustawienie nie jest już dostępne.
