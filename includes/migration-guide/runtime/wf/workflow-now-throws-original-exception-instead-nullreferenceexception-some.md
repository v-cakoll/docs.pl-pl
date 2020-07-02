---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621241"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Przepływ pracy teraz zgłasza oryginalny wyjątek zamiast NullReferenceException w niektórych przypadkach

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 i starszych wersjach, gdy metoda Execute działania przepływu pracy zgłasza wyjątek z <code>null</code> wartością <xref:System.Exception.Message> właściwości, środowisko uruchomieniowe przepływu pracy system. Activities generuje <xref:System.NullReferenceException?displayProperty=fullName> , maskowanie oryginalnego wyjątku. W .NET Framework 4,7 został zgłoszony poprzednio zamaskowany wyjątek.

#### <a name="suggestion"></a>Sugestia

Jeśli Twój kod opiera się na obsłudze <xref:System.NullReferenceException?displayProperty=fullName> , zmień go, aby przechwytywać wyjątki, które mogą zostać zgłoszone przez działania niestandardowe.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
