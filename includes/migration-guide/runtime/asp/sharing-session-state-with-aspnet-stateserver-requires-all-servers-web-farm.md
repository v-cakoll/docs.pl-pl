---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981630"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Udostępnianie stanu sesji Asp.Net StateServer wymaga wszystkie serwery w farmie sieci web, aby użyć tej samej wersji .NET Framework

|   |   |
|---|---|
|Szczegóły|Podczas włączania <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> stanu sesji, wszystkie serwery w farmie internetowej danego musi być tę samą wersję programu .NET Framework w kolejności stanu zostać prawidłowo udostępnione.|
|Sugestia|Pamiętaj uaktualnić wersje programu .NET Framework na serwerach sieci web, które udostępnianie stanu w tym samym czasie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
