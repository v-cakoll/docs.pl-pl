---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237923"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant lub Contract.Requires\<TException> nie uważają String.IsNullOrEmpty za czysty

|   |   |
|---|---|
|Szczegóły|W przypadku aplikacji, które są przeznaczone dla programu .NET Framework 4.6.1, jeśli kontrakt niezmienny dla <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> lub kontrakt warunek wstępny dla <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> wywołuje <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metodę, nagrywarka emituje ostrzeżenie kompilatora CC1036: &quot;Wykryte wywołanie metody "System.String.IsNullOrWhteSpace(System.String)" bez [Pure] w metodzie. &quot; Jest to ostrzeżenie kompilatora, a nie błąd kompilatora.|
|Sugestia|To zachowanie zostało rozwiązane w [#339 problem gitHub](https://github.com/Microsoft/CodeContracts/issues/339). Aby wyeliminować to ostrzeżenie, można pobrać i skompilować zaktualizowaną wersję kodu źródłowego narzędzia Kontrakty kodu z [gitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Informacje o pobieraniu znajdują się u dołu strony.|
|Zakres|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
