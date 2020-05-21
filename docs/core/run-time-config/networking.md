---
title: Ustawienia konfiguracji sieci
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sieć dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761944"
---
# <a name="run-time-configuration-options-for-networking"></a>Opcje konfiguracji czasu wykonywania dla sieci

## <a name="http2-protocol"></a>Protokół HTTP/2

- Określa, czy jest włączona obsługa protokołu HTTP/2.

- Jeśli pominięto to ustawienie, obsługa protokołu HTTP/2 jest wyłączona. Jest to równoznaczne z ustawieniem wartości `false` .

- Wprowadzone w programie .NET Core 3,0.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-wyłączone<br/>`true`-włączone |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-wyłączone<br/>`1`-włączone |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- Określa, czy mają być <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> używane <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> lub starsze stosy protokołu HTTP ( <xref:System.Net.Http.WinHttpHandler> w systemach Windows i `CurlHandler` , wewnętrzna Klasa zaimplementowana w [libcurl](https://curl.haxx.se/libcurl/), w systemie Linux).

  > [!NOTE]
  > Możesz używać interfejsów API sieci wysokiego poziomu zamiast bezpośredniego tworzenia wystąpienia <xref:System.Net.Http.HttpClientHandler> klasy. To ustawienie wpływa również na to, który stos protokołu HTTP jest używany przez interfejsy API sieci wysokiego poziomu, w tym <xref:System.Net.Http.HttpClient> i [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).

- Jeśli pominięto to ustawienie, program <xref:System.Net.Http.HttpClientHandler> używa <xref:System.Net.Http.SocketsHttpHandler> . Jest to równoznaczne z ustawieniem wartości `true` .

- To ustawienie można skonfigurować programowo, wywołując <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metodę.

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Net.Http.UseSocketsHttpHandler` | `true`-umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`false`-umożliwia korzystanie z programu <xref:System.Net.Http.WinHttpHandler> w systemie Windows lub [libcurl](https://curl.haxx.se/libcurl/) w systemie Linux |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-umożliwia korzystanie z<xref:System.Net.Http.SocketsHttpHandler><br/>`0`-umożliwia korzystanie z programu <xref:System.Net.Http.WinHttpHandler> w systemie Windows lub [libcurl](https://curl.haxx.se/libcurl/) w systemie Linux |

> [!NOTE]
> Począwszy od platformy .NET 5, `System.Net.Http.UseSocketsHttpHandler` ustawienie nie jest już dostępne.
