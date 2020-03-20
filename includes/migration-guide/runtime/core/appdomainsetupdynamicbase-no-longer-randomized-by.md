---
ms.openlocfilehash: 3f553f95941eaf36cf335e9765a670a05bd157f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858466"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase nie jest już randomizowane przez UseRandomizedStringHashAlgorithm

|   |   |
|---|---|
|Szczegóły|Przed .NET Framework 4.6 wartość <xref:System.AppDomainSetup.DynamicBase> będzie randomizowana między domenami aplikacji lub między procesami, jeśli UseRandomizedStringHashAlgorithm została włączona w pliku konfiguracyjnym aplikacji. Począwszy od programu .NET Framework <xref:System.AppDomainSetup.DynamicBase> 4.6, zwróci stabilny wynik między różnymi wystąpieniami uruchomionej aplikacji i między różnymi domenami aplikacji. Bazy dynamiczne będą nadal się różnić w przypadku różnych aplikacji; ta zmiana usuwa tylko losowy element nazewnictwa dla różnych wystąpień tej samej aplikacji.|
|Sugestia|Należy pamiętać, <code>UseRandomizedStringHashAlgorithm</code> że włączenie <xref:System.AppDomainSetup.DynamicBase> nie spowoduje losowania. Jeśli wymagana jest losowa baza, musi być wyprodukowana w kodzie aplikacji, a nie za pośrednictwem tego interfejsu API.|
|Zakres|Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
