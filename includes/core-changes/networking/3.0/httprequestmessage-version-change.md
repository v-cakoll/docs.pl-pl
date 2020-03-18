---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451897"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna httprequestmessage.version zmieniono na 1.1

Wartość domyślna <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> właściwości została zmieniona z 2.0 na 1.1.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

W .NET Core 1.0 do 2.0 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> domyślną wartością właściwości jest 1.1. Począwszy od .NET Core 2.1, został zmieniony na 2.1.

Począwszy od .NET Core 3.0, domyślny <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> numer wersji zwrócony przez właściwość jest ponownie 1.1.

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj kod, jeśli <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zależy od właściwości zwracającej domyślną wartość 2.0.

#### <a name="category"></a>Kategoria

Networking

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
