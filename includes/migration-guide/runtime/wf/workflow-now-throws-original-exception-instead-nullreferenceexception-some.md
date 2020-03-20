---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802513"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Przepływ pracy zgłasza teraz oryginalny wyjątek zamiast NullReferenceException w niektórych przypadkach

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.2 i wcześniejszych wersjach, gdy Execute metoda działania <code>null</code> przepływu pracy <xref:System.Exception.Message> zgłasza wyjątek o wartości właściwości, System.Activities Środowisko uruchomieniowe przepływu pracy zgłasza <xref:System.NullReferenceException?displayProperty=name>, maskowanie oryginalnego wyjątku. W .NET Framework 4.7 zostanie zgłoszony poprzednio zamaskowany wyjątek.|
|Sugestia|Jeśli kod opiera się <xref:System.NullReferenceException?displayProperty=name>na obsłudze , zmień go, aby złapać wyjątki, które mogą być generowane z działań niestandardowych.|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
