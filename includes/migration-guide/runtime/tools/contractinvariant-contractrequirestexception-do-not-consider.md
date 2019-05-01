---
ms.openlocfilehash: 3cff9bfbb1adb6004921903276d75f641c7e703c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763964"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant lub Contract.Requires\<TException > należy wziąć pod uwagę String.IsNullOrEmpty być czysty

|   |   |
|---|---|
|Szczegóły|Dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.1, jeśli niezmiennej kontrakt dla <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> lub kontrakt warunek wstępny dla <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> wywołania <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody dysków emituje ostrzeżenia CC1036 kompilatora: &quot;Wykryto wywołanie metody <xref:System.String.IsNullOrWhiteSpace%2A?displayProperty=nameWithType> bez [czystej] w metodzie.&quot; Są to ostrzeżenia kompilatora, nie błędu kompilatora.|
|Sugestia|To zachowanie zostało rozwiązane w [339 # problem usługi GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Aby usunąć to ostrzeżenie, możesz pobrać i skompilować zaktualizowaną wersję kodu źródłowego narzędzia kontrakty kodu z [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Pobierz informacje znajdują się w dolnej części strony.|
|Zakres|Mały|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
