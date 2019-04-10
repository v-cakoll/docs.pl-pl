---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235459"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a>Metoda Replace w adresach URL OData jest domyślnie wyłączony

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, metoda Replace w adresach URL OData jest domyślnie wyłączona. Gdy Zastąp OData jest wyłączona (teraz domyślnie), wszystkie żądania użytkowników, w tym funkcje replace, (które są rzadko) zakończy się niepowodzeniem.|
|Sugestia|Jeśli wymagana jest metoda replace (czyli rzadko), można ponownie włączyć za pomocą ustawień konfiguracji (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>). Jednak metoda włączone zastępowanie można otworzyć luk w zabezpieczeniach i powinna być używana tylko po dokładnej przeglądu.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
