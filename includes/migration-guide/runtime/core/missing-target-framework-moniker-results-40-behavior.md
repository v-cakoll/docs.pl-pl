---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620257"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Brak monikera platformy docelowej w wyniku 4,0

#### <a name="details"></a>Szczegóły

Aplikacje bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> zastosowania na poziomie zestawu zostaną automatycznie uruchomione przy użyciu semantyki (osobliwości) .NET Framework 4,0. W celu zapewnienia wysokiej jakości zaleca się, aby wszystkie pliki binarne były jawnie przypisane do <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> wskazania wersji .NET Framework, z których zostały skompilowane. Należy zauważyć, że użycie monikera platformy docelowej w pliku projektu spowoduje automatyczne zastosowanie przez program MSBuild <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> .

#### <a name="suggestion"></a>Sugestia

<xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>Powinien być dostarczony przez dodanie atrybutu bezpośrednio do zestawu lub przez określenie platformy docelowej w [pliku projektu lub graficznego interfejsu użytkownika programu Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
