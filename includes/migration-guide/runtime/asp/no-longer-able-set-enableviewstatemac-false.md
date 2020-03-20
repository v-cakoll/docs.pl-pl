---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803204"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Nie można już ustawić opcji EnableViewStateMac na false

|   |   |
|---|---|
|Szczegóły|ASP.NET nie pozwala już deweloperom na określenie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Kod uwierzytelniania wiadomości o stanie widoku (MAC) jest teraz wymuszany dla wszystkich żądań ze stanem widoku osadzonego. Dotyczy to tylko aplikacji, które jawnie <code>false</code> ustawić EnableViewStateMac właściwość dotyczy.|
|Sugestia|EnableViewStateMac należy przyjąć, że jest true, a wszelkie wynikające błędy MAC muszą być rozwiązane (jak wyjaśniono w [niniejszych wytycznych,](https://support.microsoft.com/kb/2915218)który zawiera wiele rozdzielczości w zależności od specyfiki tego, co jest przyczyną błędów MAC).|
|Zakres|Duży|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
