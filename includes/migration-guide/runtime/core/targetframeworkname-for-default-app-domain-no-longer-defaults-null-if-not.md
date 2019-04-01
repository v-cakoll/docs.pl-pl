---
ms.openlocfilehash: f221f923381d874e1d9e8b420811a770d86f7578
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761371"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName dla domyślnej domeny aplikacji nie jest już domyślnie przyjmuje wartość null Jeśli nie zostanie ustawiona

|   |   |
|---|---|
|Szczegóły|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Została wcześniej wartości null w domyślnej domeny aplikacji, o ile nie została jawnie ustawiona. Począwszy od 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> właściwość dla domyślnej domeny aplikacji będzie mieć wartość domyślną, pochodną TargetFrameworkAttribute (jeśli istnieje). Domeny inne niż domyślne aplikacji będą w dalszym ciągu dziedziczą ich <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> z domyślnej domeny aplikacji (co nie jest domyślnie ustawiana na wartość null w wersji 4.6) o ile nie jest jawnie przesłaniana.|
|Sugestia|Kod powinien zostać zaktualizowany, aby nie są zależne od <xref:System.AppDomainSetup.TargetFrameworkName> przyjęto wartość domyślną wartość null. Jeśli jest to konieczne, właściwość ta w dalszym ciągu ma wartość null, może być jawnie ustawiona na tę wartość.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

