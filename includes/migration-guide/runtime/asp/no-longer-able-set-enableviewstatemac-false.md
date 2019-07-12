---
ms.openlocfilehash: 78f4d533f1efdc8d43a9ab96508b84a77e3260bc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803204"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Nie będzie możliwe ustawienie EnableViewStateMac na wartość false

|   |   |
|---|---|
|Szczegóły|Program ASP.NET nie zezwala już deweloperom określenie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Wyświetl stan kodu uwierzytelniania wiadomości (MAC) jest teraz wymuszane na wszystkie żądania z osadzonych widoku stanu. Tylko te aplikacje, które jawnie ustawione właściwości EnableViewStateMac <code>false</code> dotyczy problem.|
|Sugestia|EnableViewStateMac musi być zakłada się, że wartość true, a wszystkie wynikowe błędy MAC musi być rozwiązane (zgodnie z opisem w [Niniejsze wskazówki](https://support.microsoft.com/kb/2915218), który zawiera wielu rozdzielczości w zależności od tego, co jest przyczyną błędów MAC szczegółowych).|
|Scope|Duży|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|

