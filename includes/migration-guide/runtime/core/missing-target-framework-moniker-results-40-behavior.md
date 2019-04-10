---
ms.openlocfilehash: 29b8feb7959c718391b963c8402b97351b93fa49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235788"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Brak Moniker platformy docelowej powoduje zachowanie 4.0

|   |   |
|---|---|
|Szczegóły|Aplikacje bez <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> zastosowano zestaw będzie poziomu automatycznego uruchamiania, za pomocą semantyki (Osobliwości) .NET Framework 4.0. W celu zapewnienia wysokiej jakości, zalecane jest, że wszystkie pliki binarne można jawnie przypisać z <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> wskazujący wersję programu .NET Framework zostały skompilowane. Należy pamiętać, że korzystanie z monikerem platformy docelowej w pliku projektu spowoduje, że program MSBuild, aby automatycznie zastosować <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name>.|
|Sugestia|A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> powinien być dostarczony, poprzez dodanie atrybutu bezpośrednio do zestawu lub określanie platformy docelowej, w [pliku projektu lub za pomocą programu Visual Studio projektu graficznego interfejsu użytkownika właściwości](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).|
|Zakres|Duży|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
