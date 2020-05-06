---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859618"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>Klient WebClient. CancelAsync nie zawsze anuluje natychmiast

Począwszy od platformy .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> wywołanie nie anuluje żądania natychmiast, jeśli odpowiedź została rozpoczęta do pobrania.

#### <a name="change-description"></a>Zmień opis

Wcześniej wywołanie <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zostało anulowane. Począwszy od platformy .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> wywołanie anuluje żądanie natychmiast tylko wtedy, gdy odpowiedź nie rozpoczęła pobierania. Jeśli odpowiedź została rozpoczęta do pobrania, żądanie zostanie anulowane tylko po odczytaniu kompletnej odpowiedzi.

Ta zmiana została zaimplementowana <xref:System.Net.WebClient> , ponieważ interfejs API jest przestarzały <xref:System.Net.Http.HttpClient>.

#### <a name="version-introduced"></a>Wprowadzona wersja

2.0

#### <a name="recommended-action"></a>Zalecana akcja

Użyj <xref:System.Net.Http.HttpClient?displayProperty=fullName> klasy zamiast <xref:System.Net.WebClient?displayProperty=fullName>, która jest przestarzała.

#### <a name="category"></a>Kategoria

Networking

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
