---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620170"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Nie można już ustawić EnableViewStateMac na FAŁSZ

#### <a name="details"></a>Szczegóły

ASP.NET nie pozwala już deweloperom na określanie <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> lub <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> . Kod uwierzytelniania komunikatów o stanie (MAC) jest teraz wymuszany dla wszystkich żądań z osadzonym stanem widoku. Dotyczy to tylko aplikacji, które jawnie ustawili Właściwość EnableViewStateMac <code>false</code> .

#### <a name="suggestion"></a>Sugestia

Należy przyjąć, że EnableViewStateMac należy mieć wartość true, a wszystkie wynikowe błędy w systemie MAC muszą zostać rozwiązane (jak wyjaśniono w [niniejszych wskazówkach](https://support.microsoft.com/kb/2915218), które zawierają wiele rozwiązań w zależności od tego, co powoduje błędy w przypadku komputerów Mac).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Duży|
|Wersja|4.5.2|
|Typ|Środowisko uruchomieniowe|
