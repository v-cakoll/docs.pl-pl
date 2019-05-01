---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664061"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Nie będzie możliwe ustawienie EnableViewStateMac na wartość false

|   |   |
|---|---|
|Szczegóły|Program ASP.NET nie zezwala już deweloperom określenie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Wyświetl stan kodu uwierzytelniania wiadomości (MAC) jest teraz wymuszane na wszystkie żądania z osadzonych widoku stanu. Tylko te aplikacje, które jawnie ustawione właściwości EnableViewStateMac <code>false</code> dotyczy problem.|
|Sugestia|EnableViewStateMac musi być zakłada się, że wartość true, a wszystkie wynikowe błędy MAC musi być rozwiązane (zgodnie z opisem w [Niniejsze wskazówki](https://support.microsoft.com/kb/2915218), który zawiera wielu rozdzielczości w zależności od tego, co jest przyczyną błędów MAC szczegółowych).|
|Zakres|Duży|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
