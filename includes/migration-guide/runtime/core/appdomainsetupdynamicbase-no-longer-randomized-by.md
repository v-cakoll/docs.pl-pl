---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621289"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup. DynamicBase nie jest już losowo określana przez UseRandomizedStringHashAlgorithm

#### <a name="details"></a>Szczegóły

Przed .NET Framework 4,6 wartość zostanie przetworzona <xref:System.AppDomainSetup.DynamicBase> losowo między domenami aplikacji lub między procesami, jeśli UseRandomizedStringHashAlgorithm został włączony w pliku konfiguracji aplikacji. Począwszy od .NET Framework 4,6, <xref:System.AppDomainSetup.DynamicBase> zwróci stabilny wynik między różnymi wystąpieniami aplikacji i między różnymi domenami aplikacji. Dynamiczne bazy nadal różnią się w zależności od różnych aplikacji; Ta zmiana powoduje jedynie usunięcie losowego elementu nazewnictwa dla różnych wystąpień tej samej aplikacji.

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że włączenie <code>UseRandomizedStringHashAlgorithm</code> nie spowoduje <xref:System.AppDomainSetup.DynamicBase> losowego uruchamiania. Jeśli jest wymagana Losowa baza, należy ją utworzyć w kodzie aplikacji, a nie za pośrednictwem tego interfejsu API.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
