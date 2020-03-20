---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859152"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath zgłasza NullReferenceException

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.2 środowisko <code>T:System.NullReferenceException</code> wykonawcze zgłasza <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> podczas pobierania wartości zawierającej znaki null. W .NET Framework 4.6.1 i wcześniejszych wersjach <code>T:System.ArgumentNullException</code>środowisko uruchomieniowe zgłasza .|
|Sugestia|Możesz wykonać jedną z dalszych działań, aby odpowiedzieć na tę zmianę:<ul><li><code>T:System.NullReferenceException</code> Obsługa, jeśli aplikacja jest uruchomiona w programie .NET Framework 4.6.2.</li><li>Uaktualnij do programu .NET Framework 4.7, który przywraca <code>T:System.ArgumentNullException</code>poprzednie zachowanie i rzuca plik .</li></ul>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
