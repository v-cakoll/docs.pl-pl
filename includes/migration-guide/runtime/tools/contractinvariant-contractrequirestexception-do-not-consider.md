---
ms.openlocfilehash: 794e43826af8f443a2cbb43b41f233766adc9dfd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802969"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant lub Contract.Requires\<TException > należy wziąć pod uwagę String.IsNullOrEmpty być czysty

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, jeśli niezmiennej kontrakt dla <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> lub kontrakt warunek wstępny dla <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> wywołania <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody dysków emituje ostrzeżenia CC1036 kompilatora: &quot;Wykryto wywołanie metody "System.String.IsNullOrWhteSpace(System.String)" bez [czystej] w metodzie.&quot; Są to ostrzeżenia kompilatora, nie błędu kompilatora.|
|Sugestia|To zachowanie zostało rozwiązane w [339 # problem usługi GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Aby usunąć to ostrzeżenie, możesz pobrać i skompilować zaktualizowaną wersję kodu źródłowego narzędzia kontrakty kodu z [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Pobierz informacje znajdują się w dolnej części strony.|
|Scope|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

