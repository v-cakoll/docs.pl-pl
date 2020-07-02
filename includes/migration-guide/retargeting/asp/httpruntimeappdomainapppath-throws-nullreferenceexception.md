---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617544"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime. AppDomainAppPath zgłasza NullReferenceException

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 środowisko uruchomieniowe zgłasza `T:System.NullReferenceException` wartość przy pobieraniu wartości zawierającej `P:System.Web.HttpRuntime.AppDomainAppPath` znaki null. W .NET Framework 4.6.1 i wcześniejszych wersji środowisko uruchomieniowe zgłasza `T:System.ArgumentNullException` .

#### <a name="suggestion"></a>Sugestia

Aby odpowiedzieć na tę zmianę, możesz wykonać jedną z następujących czynności:

- Obsługuj `T:System.NullReferenceException` aplikację, jeśli aplikacja jest uruchomiona na .NET Framework 4.6.2.
- Uaktualnij do .NET Framework 4,7, który przywraca poprzednie zachowanie i zgłasza `T:System.ArgumentNullException` .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
