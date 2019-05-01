---
ms.openlocfilehash: 6c2c6422ca4d426fcc2ff5827a2387abb5578e3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091707"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>Podczas analizowania System.Uri działa zgodnie z RFC 3987

|   |   |
|---|---|
|Szczegóły|Podczas analizowania identyfikatora URI zmienił się na kilka sposobów, w programie .NET Framework 4.5. Należy jednak pamiętać, że zmiany te dotyczą tylko kodu przeznaczone dla .NET Framework 4.5. Jeżeli binarne docelowych programu .NET Framework 4.0, stare zachowanie będą przestrzegane. Zmiany do identyfikatora URI analizy w programie .NET Framework 4.5 obejmują:<ul><li>Analizy identyfikatora URI wykona normalizacji i sprawdzanie zgodnie z regułami z najnowszą IRI RFC 3987 znaków.</li><li>Formuła normalizacji Unicode C będzie można wykonać tylko na część identyfikatora URI hosta.</li><li>Nieprawidłowy mailto: Identyfikatory URI teraz spowoduje, że wyjątek.</li><li>Końcowe kropki na końcu segmentu ścieżki, zostaną zachowane.</li><li><code>file://</code> Identyfikatory URI wyprowadza <code>?</code> znaków.</li><li>Znaki kontrolne Unicode <code>U+0080</code> za pośrednictwem <code>U+009F</code> nie są obsługiwane.</li><li>Znak przecinka <code>,</code> lub <code>%2c</code> nie są automatycznie o niezmienionym znaczeniu.</li></ul>|
|Sugestia|W przypadku potrzeby (często nie są one) stare semantyki analizy identyfikatora URI programu .NET Framework 4.0, mogą one używane przez przeznaczonych dla programu .NET Framework 4.0. Można to zrobić za pomocą <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> w zestawie lub za pośrednictwem interfejsu użytkownika systemu projektu programu Visual Studio na stronie "właściwości projektu".|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|
