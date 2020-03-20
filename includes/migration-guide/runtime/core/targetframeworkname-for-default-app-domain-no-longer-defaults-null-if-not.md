---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858617"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName dla domyślnej domeny aplikacji nie jest już domyślnie null, jeśli nie jest ustawiona

|   |   |
|---|---|
|Szczegóły|Wcześniej <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> wartość null była null w domyślnej domenie aplikacji, chyba że została jawnie ustawiona. Począwszy od 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> właściwość dla domyślnej domeny aplikacji będzie miała wartość domyślną pochodną targetframeworkattribute (jeśli jest obecny). Domeny aplikacji inne niż domyślne <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> będą nadal dziedziczyć z domyślnej domeny aplikacji (która nie będzie domyślnie null w 4.6), chyba że zostanie jawnie zastąpiona.|
|Sugestia|Kod powinien zostać zaktualizowany, aby nie był zależny <xref:System.AppDomainSetup.TargetFrameworkName> od niewykonania zobowiązania do wartości null. Jeśli jest wymagane, że ta właściwość w dalszym ciągu do oceny null, można jawnie ustawić tę wartość.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
